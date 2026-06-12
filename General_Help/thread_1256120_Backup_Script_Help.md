---
title: "Backup Script Help"
date: 2009-09-02
forum: General Help
---

### Post by Spyder89 on 2009-09-02
Here is what I need to do. 

I need to safely shutdown my virtual machines and then backup the /Virtual \Machines directory and then start the virtual machines back up. I need to do this on a monthly basis. 

Here is what I have: 
2 Dell servers running Ubuntu 8.04 64B Server as host operating system. VMware Server 2.0 Final installed. Both of these servers are running 3 Virtual Machines(2 Ubuntu based and 1 Windows XP based). 

All help is greatly appreciated.

---

### Post by aeiah on 2009-09-02
well if you can control vmware from the commandline you can just write a script that:

- shuts down virtual machines
- runs backup
- starts virtual machines


what method are you using to backup? snapshots?

---

### Post by e24ohm on 2009-09-02
> **Spyder89 said:**
> Here is what I need to do. 

I need to safely shutdown my virtual machines and then backup the /Virtual \Machines directory and then start the virtual machines back up. I need to do this on a monthly basis. 

Here is what I have: 
2 Dell servers running Ubuntu 8.04 64B Server as host operating system. VMware Server 2.0 Final installed. Both of these servers are running 3 Virtual Machines(2 Ubuntu based and 1 Windows XP based). 

All help is greatly appreciated.i would use backula or Rsync with a nice script to run "tar" and the "-u" switch to only up date the change/updated files.

---

### Post by Spyder89 on 2009-09-02
> **aeiah said:**
> well if you can control vmware from the commandline you can just write a script that:

- shuts down virtual machines
- runs backup
- starts virtual machines


what method are you using to backup? snapshots?

I would like to use tar to do the backup. It is easy and seems to work good.

---

### Post by Spyder89 on 2009-09-02
> **e24ohm said:**
> i would use backula or Rsync with a nice script to run "tar" and the "-u" switch to only up date the change/updated files.

Those programs are both great programs but are not going to help my situation. 

I should have specified better earlier. The problem I am having is powering off and powering on the virtual machines. I need to power them down because backup will not complete correctly if the virtual machine is running. When the virtual machines are running the files in the /Virtual Machine directories are being changed.

---

### Post by Spyder89 on 2009-09-03
Discovered the vmrun command. It will allow me to start and stop the virtual machines. Now all I have to do is learn how to write scripts(wooohooo!!!).

---

### Post by e24ohm on 2009-09-03
> **Spyder89 said:**
> Discovered the vmrun command. It will allow me to start and stop the virtual machines. Now all I have to do is learn how to write scripts(wooohooo!!!).that is tight. You can build a bash script to kill the vm, run the backup, the start the vm. What switch are you using to kill the vm? I want to play around with this.

---

### Post by Spyder89 on 2009-09-03
The string is this:

vmrun -T server -h [https://IPADDRESS:8333/sdk](https://IPADDRESS:8333/sdk) -u root -p xxxxxx stop "[DATASTORE NAME] ubuntu/ubuntu.vmx" soft

Stop can be replaced with start(you will have to remove the word soft at the end though). 

IPADDRESS will have to be replaced with either the ipaddress of the machine or the hostname. 

DATASTORE NAME has to be replaced with your datastore name. 

"ubuntu/ubuntu.vmx" is the directories after the datastore.

---

