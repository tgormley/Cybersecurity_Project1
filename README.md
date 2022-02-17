## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

<img width="750" alt="Network_Diagram" src="https://github.com/tgormley/Cybersecurity_Project1/blob/main/Diagrams/Project1.drawio%20(1).png?raw=true">

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the files may be used to install only certain pieces of it, such as Filebeat.

  etc/ansible/filebeat-playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient, in addition to restricting traffic to the network.
- A load balancer defends an organization against DDOS (distributed denial-of-service) attacks. It does this by shifting attack traffic from the corporate server to a public cloud provider.
- A jumpbox is a secure computer that all admins first connect to before launching any administrative task or use as an origination point to connect to other servers or untrusted environments.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
- Filebeat is useful for forwarding and centralizing log data. Filebeat monitors the log files or locations that are specified, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
- Metricbeat takes the metrics and statistics that it collects and ships them to the output that is specified, such as Elasticsearch or Logstash.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux (ubuntu 18.04)  |
| Web-1    | Server   | 10.1.0.7   | Linux (ubuntu 18.04)  |
| Web-2    | Server   | 10.1.0.8   | Linux (ubuntu 18.04)  |
| Elk-VM   | Kibana   | 10.2.0.4   | Linux (ubuntu 18.04)  |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox machine and Elk machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

home (personal) ip address

Machines within the network can only be accessed by SSH.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_
The jumpbox is used to access the Elk VM, private IP: 10.1.0.4
A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |    Yes              | home ip              |
|  Elk-VM  |    Yes              | home ip              |
|   Web-1  |     No              | 10.1.0.4             |
|   Web-2  |     No              | 10.1.0.4             |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because 
it allows for predictable and consistent configurations. It also helps considerably with the representation of Infrastructure as Code (IAC). IAC involves provisioning and management of computing infrastructure and related configuration through machine-processable definition files.


The playbook implements the following tasks:
- Install docker.io and python3-pip packages with the apt module
- Install Docker Module with the pip module
- Increase Virtual Memory: sysctl -w vm.max_map_count=262144
- Use more memory with sysctl module
- Download and launch a docker elk container (sebp/elk:761)

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

 <img width="675" alt="docker_ps" src="https://github.com/tgormley/Cybersecurity_Project1/blob/main/docker_ps_output.png?raw=true">

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

Sources:
https://avinetworks.com/what-is-load-balancing/#:~:text=Load%20Balancing%20plays%20an%20important,to%20a%20public%20cloud%20provider.
https://www.csoonline.com/article/2612700/security-jump-boxes-improve-security-if-you-set-them-up-right.html#:~:text=Jump%20boxes%20are%20normally%20centrally,are%20the%20more%20secure%20option.
https://www.whizlabs.com/blog/ansible-advantages-and-disadvantages/#:~:text=Ansible%20automation%20helps%20considerably%20with,through%20machine%2Dprocessable%20definition%20files.


