## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/we-merrill75/Cybersecurity-Project-1/blob/main/Elk_Stack_Topology.drawio.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to recreate the entire deployment pictured above. Alternatively, select portions of the .yml files may be used to install only certain pieces of it, such as Filebeat.

https://github.com/we-merrill75/Cybersecurity-Project-1/blob/main/config-Elk-vm.yml
https://github.com/we-merrill75/Cybersecurity-Project-1.git

This document contains the following details:
  - Description of the Topology
  - Access Policies
  - ELK Configuration
   - Beats in Use
   - Machines Being Monitored
  - How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, and have restricted access to the network.
Load balancers increase capacity, and availability by distributing incoming data between multiple web servers. 
Jump boxes make updating, maintaining, and servicing multiple systems quicker and easier. They also provide an additional layer of security.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the event logs and system metrics.

Filebeat monitors the log files (or specified locations), collects the log events, and forwards them to either Elasticsearch/Logstash/Kibana for indexing.

Metricbeat monitors servers by collecting metrics from the system and services running on the server. The information that it collects is sent to a SIEM tool like ELK-Stack. 

The configuration details of each machine may be found below.

| Name      | Function  | IP Address      | Operating System  |
|---------- |---------- |-----------------|-------------------|
| Jump Box  |Gateway    | 20.124.125.77   | Linux             |
| Web 1	    |Web Server | 10.0.0.5        | Linux             |
| Web 2     |Web Server | 10.0.0.6        | Linux             |
| ELK Server|Data       | 10.1.0.4        | Linux             |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

174.63.0.246

Machines within the network can only be accessed by Jump Box 20.124.125.77. The Elk Server can have access from personal IP address through port 5601.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses            |
|----------|---------------------|---------------------------------|
| Jump Box |     Yes             | 174.63.0.246                    |
| Web 1    |     No              | 10.1.0.4                        |
| Web2     |     No              | 10.1.0.4                        |
| Elk Server  |  yes             | 10.1.0.4                        |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it is simple, reliable, efficient, and consistent for configuration management, application deployment, and orchestration (bringing different elements into a beautifully run whole operation).
 
Ansible automation helps considerably with the representation of Infrastructure as Code (IAC). IAC involves provisioning and managing computing infrastructure and related configurations through machine-processable definition files.

The  Elk playbook implements the following tasks:
  - install docker
  - install pip3
  - install docker python module
  - increase virtual memory
  - use more memory
  - download and launch a docker elk container.

The steps of the ELK installation are laid out below:
  - use ssh to access the Jump Box from my host machine
  - using Ansible, create a container with a randomly assigned name; (wizardly_sammet)
  - attach container to the jumpbox through which the container can be accessed
  - run the playbook to install elk in the container
 
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![image](https://user-images.githubusercontent.com/99710515/159385797-96926b7c-6ed7-4980-8307-f09dd51d007d.png)(Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
  -10.0.0.5 Web 1
  -10.0.0.6 Web-2

I installed the following Beats on these machines:
  -Metricbeat
  -Filebeat

These Beats allow the collecting of  information from each machine:
  -Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash. Metricbeat helps you monitor your servers by collecting metrics from the system and services running on the server, such as: Apache
-Installed as an agent on your servers, Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing. Here’s how Filebeat works: When you start Filebeat, it starts one or more inputs that look in the locations you’ve specified for log data

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Metricbeat configuration file to the /etc/ansible.
- Update the hosts file to include the ELK server ip address.
- Run the playbook, and navigate to Kibana Metricbeat/download module to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? yaml Where do you copy it? /etc/ansible
- _Which file do you update to make Ansible run the playbook on a specific machine? HOSTS How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running? Kibana http://174.63.0.246:5601/app/kibana#/home?_g=()
get into container, then download the elk yml and then ssh into elk server
_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
