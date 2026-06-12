---
title: "Lost graphics card drivers"
date: 2010-09-20
forum: General Help
---

### Post by mick463 on 2010-09-20
Hi there i am running 10.04 64 bit and did an update today and now i do not have any graphics card drivers and my virtual box is not working at all i have tried to reinstall the drivers through the hardware drivers and get told i have to look at the 

Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

and when i try to open my virtual box i get 


Failed to open a session for the virtual machine Server 08.
Failed to open/create the internal network 'HostInterfaceNetworking-eth0' (VERR_SUPDRV_COMPONENT_NOT_FOUND).
Failed to attach the network LUN (VERR_SUPDRV_COMPONENT_NOT_FOUND).
One of the kernel modules was not successfully loaded. Make sure that no kernel modules from an older version of VirtualBox exist. Then try to recompile and reload the kernel modules by executing '/etc/init.d/vboxdrv setup' as root (VERR_SUPDRV_COMPONENT_NOT_FOUND).



Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {6375231a-c17c-464b-92cb-ae9e128d71c3}

Please some one help i have to at least get some info off the virtual box and i am a Linux beginner thank you.

---

### Post by mick463 on 2010-09-20
Hi i have fixed the virtual box problem but the graphics card problem still remains could it be that i am on a slow internet (satellite)connection.But i would like to know why i have lost them after i updated my computer. Thank you.

---

### Post by hawthornso23 on 2010-09-20
I had the identical symptoms after an upgrade and was able to fix it. The method i used is described here 

[http://ubuntuforums.org/showthread.php?t=1537869](http://ubuntuforums.org/showthread.php?t=1537869)

Good Luck

---

### Post by mick463 on 2010-09-21
Hey mate i tried what you linked me and all i get now is that i do not have a genuine package when i try to send the error report.I tried the link from [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/642518](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/642518)   

using posts 14 and 34 but i still can not get it to work any ideas Cheers Mick463.

---

