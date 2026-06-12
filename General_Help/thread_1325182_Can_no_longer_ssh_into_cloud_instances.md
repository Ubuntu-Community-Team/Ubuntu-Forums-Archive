---
title: "Can no longer ssh into cloud instances"
date: 2009-11-13
forum: General Help
---

### Post by ewgates on 2009-11-13
_[SIZE=3][FONT=Calibri]Setup: [/FONT][/SIZE]_
 

[SIZE=3][FONT=Calibri]Two Dell E6400 laptops, one setup as the front end with Cloud and Cluster Controller, the other setup as the Node. [/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]Ubuntu 9.10 64 bit server with cloud has been installed. [/FONT][/SIZE]
 
[FONT=Calibri][SIZE=3]The image is the “Ubuntu 9.10 RC – Karmic Koala (32bit) Image Version 20091022” installed from the eucalyptus login, “store” menu. I never did get the 64 bit version to run in an instance (described in a previous ubuntu forum log).[/SIZE][/FONT]
 
[SIZE=3][FONT=Calibri]The only user is admin. [/FONT][/SIZE]
 
[FONT=Calibri][SIZE=3]“euca-run-instances emi-E22D108D –k mykey –t c1.medium –n 1-4” It created two instances.[/SIZE][/FONT]
 
_[SIZE=3][FONT=Calibri]Problem Description:[/FONT][/SIZE]_
 

[SIZE=3][FONT=Calibri]I was able to ssh into an instance of the image listed above until I tried to install the ubuntu desktop. It ran out of space. I could still ssh into it, but could do nothing, including uninstall the desktop. [/FONT][/SIZE]
 
[FONT=Calibri][SIZE=3]I terminated those instances then started another one. I could not ssh into it. [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]“euca-terminate-instance i-546D08DE, i-35DF0746”[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]“euca-run-instances emi-E22D108D –k mykey –t m1.xlarge –n 1-4” It created one instance.[/SIZE][/FONT]
**[SIZE=3][FONT=Calibri]SSH error = “Permission denied (publickey)”[/FONT][/SIZE]**
[SIZE=3][FONT=Calibri]“euca-terminate-instance i-48020811”[/FONT][/SIZE]
 
[FONT=Calibri][SIZE=3]I terminated and restarted several times using different size and number of instances but still could not ssh into any of the instances. I could still SSH into the node from the front end.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]I cleared out the known_hosts file, verified that I only had one keypair available and that I was specifying that keypair when the instance was started. I verified several entries in both ssh_config and sshd_config.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]I tried to copy the public key to the instance but couldn’t figure out how to login to the instance to set it up in the .ssh directory. Isn’t this supposed to be setup for me when the instance starts anyway?[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]I found a known defect that describes a problem when the instance starts up quickly the init code can occasionally try to use the network before the network is working. The solution is to reboot the instances.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]“euca-run-instances emi-E22D108D –k mykey –t m1.large” [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]Can’t ssh into it, **SSH error = “Permission denied (publickey)”.**[/FONT][/SIZE]
[FONT=Calibri][SIZE=3]“euca-rebot-instance i-500E090F”[/SIZE][/FONT]
**[SIZE=3][FONT=Calibri]Reboot terminated the instance.[/FONT][/SIZE]**
 
[FONT=Calibri][SIZE=3]I repeated this several times, and each instance was terminated instead of rebooted.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]I found another defect that showed that sometimes the reboot command will actually terminate the instance. In my case it ALWAYS terminates the instance.[/SIZE][/FONT]
 
_[SIZE=3][FONT=Calibri]Questions:[/FONT][/SIZE]_
 
[FONT=Calibri][SIZE=3]How can I recover so that I can run an instance, ssh into it, then terminate instances for experiments?[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]What are the boundaries for an instance that runs out of space? Should I simply have created a larger instance(s) or does this mean that it thinks the hard drive is full (not likely)?[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Are there known problems with specific parameters of the “euca-run-instances” command (for example, avoid large instances)?[/SIZE][/FONT]

---

### Post by ewgates on 2009-11-19
I solved the problem by reinstalling the Ubuntu 9.10 server with cloud on the Front End.  I did not need to reinstall the Node.

---

