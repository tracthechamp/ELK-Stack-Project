# ELK-Stack-Project

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Images/MetricBeat-Dashboard
Images/SystemDashboard
Images/Welcome-To-Kibana

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

  - filebeat-playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- Load balancers distribute the traffic to multiple servers to reduce overusage of a single server. The jump box is used to
determine which virtual machine/server to connect to. It basically manages other systems.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system metrics.
- The Filebeat watches for log files and collects their events.
- The Metricbeat collects metric data from the servers to check its usage.

The configuration details of each machine may be found below.


| Name        | Function | IP Address | Operating System |
|-------------|----------|------------|------------------|
| Jump Box    | Gateway  | 10.0.0.7   | Linux            |
| ELK-Server  | Logging  | 10.1.0.4   | Linux            |
| Web-Server1 | Server   | 10.0.0.5   | Linux            |
| Web-Server2 | Server   | 10.0.0.6   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 75.137.11.120

Machines within the network can only be accessed by the jumpbox.
- I allowed the jumpbox to get to the ELK VM via the jumpbox's IP 10.0.0.7.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |     No              | 10.0.0.5 10.0.0.6    |
|          |                     |                      |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- You can run multiple tasks at once without having to run them separately.

The playbook implements the following tasks:
- Installing docker
- Installing python on the container
- Installing the image for the docker container
- Enabling the docker container service

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Images\Screenshot-Sebp

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5 and 10.0.0.6

We have installed the following Beats on these machines:
- Installed the filebeats and metricbeats on the web servers 1 (10.0.0.5) and 2 (10.0.0.6).

These Beats allow us to collect the following information from each machine:
- The Filebeat will collect system logs such as memory allocation or runtime.
- The Metricbeat will collect data from the Docker container such as CPU and memory usage.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-config.yml file to /etc/ansible/files.
- Update the hosts file to include the elk host that includes the private IP of the ELK server. Separate that by categorizing the private IPs of the web server 1 and 2 under web host.
- Run the playbook, and navigate to http://40.80.157.250:5601/app/kibana to check that the installation worked as expected.

