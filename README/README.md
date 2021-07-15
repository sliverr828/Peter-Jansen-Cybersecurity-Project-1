## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

README/Images/Project 1.drawio

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the pentest.yml and install-elk.yml files may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available to authorized users, in addition to restricting access to the network.


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system metrics.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.6   | Linux            |
| DVWA-VM1 | VM       | 10.0.0.7   | Linux            |
| DVWA-VM2 | VM       | 10.0.0.9   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:  75.73.104.116

Machines within the network can only be accessed by the ip address 75.73.104.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | 75.73.104            |
| DVWA-VM1 | No                  | 10.0.0.6             |
| DVWA-VM2 | No                  | 10.0.0.6             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because whenever there is a new machine added to the group, all of the actions in the playbook are performed automaticly when the playbook is run.

The playbook implements the following tasks:
- Install Docker
- Install Python-Pip
- Install Docker Module
- Increase Virtual Memory to 262144
- Download and launch a docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

README/Images/Docker-PS-Screenshot.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines: 10.0.0.7, 10.0.0.9

We have installed the following Beats on these machines: Filebeat and Metricbeat.

These Beats allow us to collect the following information from each machine:
Filebeat is able to collect log data from machines and create a visual representation of the results, which will allow us to effectivly monitor various kinds of traffic on the machines.  Metricbeat performs a similar function but instead of log files, it collects system metrics. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the pentest.yml file to etc/ansible.
- Update the hosts file to include the ip of the new machine that you wish to be added. Be sure to update the correct list in the hosts file.  In this case, we are looking to update the list of machines controled by the pentest.yml playbook, so we would edit the webservers list.
- Run the playbook, and navigate to 13.82.136.49:5601 to check that the installation worked as expected.
