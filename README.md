# Will_Bearss_Elk_Stack_Project

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

[Red Team Network Diagram](https://drive.google.com/file/d/1kEkQKz0jB6I3B3TRU2ZTWuarMO4ZYv7k/view?usp=sharing)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the [Filebeat Playbook]https://github.com/will8791/Will_Bearss_Elk_Stack_Project/blob/master/Ansible/filebeat%20Config.rtffile may be used to install only certain pieces of it, such as Filebeat.

[Configuration & Playbook Files](https://github.com/will8791/Will_Bearss_Elk_Stack_Project/tree/master/Ansible)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly **available**, in addition to **restricting** access to the network.
What aspects of Security do load balancers protect? 
**They Help Elminate points of failure, they protect agains DDoS attacks, they authenticate User access, and make it harder to exhaust resources.**
What is the advantage of a Jumpbox?
**A jumpbox is a secure computer or vm that admins can use to first connect to before launching any administrative tasks.  It also can be used as an origination point to connect to other servers or untrusted environments.  It is a secure workstation, all around.**

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the **files** and system **logs**.
- What does Filebeat watch for?_
**It watches for the log files or locations that you, the user, specify, it collects log events, and also forwards them either to Elasticsearch or Logstash for indexing.**
- What does Metricbeat record?_
**It records metrics from system and services running on the machine that is being monitored.**

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box |Gateway   | 10.0.0.5   | Linux            |
| DVWA-VM 1|Pentesting| 10.0.0.6   | Linux            |
| ELKServer|Monitoring| 10.0.0.11  | Linux            |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the **jumpbox (host)** machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- **108.2.200.199**_

Machines within the network can only be accessed by **ssh**.
- Which machine did you allow to access your ELK VM? What was its IP address?_
**Jumpbox (Test Machine) IP: 10.0.05**

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 |108.2.200.199         |
| DVWA     | No                  |10.0.0.5              |
| ELK      | Yes                 |10.0.0.5/108.2.200.199|

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?_
**It saves time in the long run by having many things executed at once, in one command, once the ansible is complete.  It is also free.**

The playbook implements the following tasks:
- In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- **Add Elk Server to ansible.cfg file.**
- **Install elk_playbook.yml file.**
- **Run Newly created playbook file.**
- **Run 'sudo docer ps' to ensure Elk is loaded and enabled.**

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
[Elk Server Data](https://github.com/will8791/Will_Bearss_Elk_Stack_Project/blob/master/images/Elk%20Server%20Data.png!)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- List the IP addresses of the machines you are monitoring_
**DVWA - 23.96.61.165/10.0.0.6**

We have installed the following Beats on these machines:
- Specify which Beats you successfully installed.
**Meticbeat & Filebeat.**

These Beats allow us to collect the following information from each machine:
- In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
**Filebeat monitors the log files or locations that you specify, collects log events, and forwards them to either Elasticsearch of Logstash for indexing.  Filebeat can be used to monitor user login successes or failures or changes that have been made to the system.**

**Metricbeat collects metrics from the operating system and other services running on the server.  Metricbeat can show statistics on CPU usage, memory, and networks.**

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the **source** file to **destination**.
- Update the **configuration** file to include **the ip of your elk server.**
- Run the playbook, and navigate to **elk server** to check that the installation worked as expected.

_ Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
**The playbook is metricbeat.yml.  This file is copied to /etc/metricbeat/meticbeat.yml on the ELK server.**

- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
**The ansible-configuration file is updated to make the Ansible run the playbook on a specific machine. In the configuration file you specify (elkservers) and the ELK server IP address. Filebeat points to the (webservers) IP address.**

- _Which URL do you navigate to in order to check that the ELK server is running?
**http://(public IP of ELK server):5601**

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
