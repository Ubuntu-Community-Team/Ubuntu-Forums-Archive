---
title: "xManager &amp; remote desktop -Ubuntu as non root user"
date: 2009-08-30
forum: General Help
---

### Post by ralusrpub09 on 2009-08-30
Hi, 

I have opends installed under root/opends and all executables are under /root/opends/bin.
I need to run this UI version of admin tool using xManager from remote machine (x forward) as another user other than root. I have "sudo su" and can type my password to switch to root.

When I tried using xManager 2.0 to run this executables as non root user, it says permission denied. In this case, there is no provision to enter "sudo su" in xManager. But when tries to run as root, it asks for root password which I don't have. 
I have created a group called "opends" and added my user id& root into this group. Given all rx -R permission to this opends directory. But still can't run it as non root user. is it becoz of opends installed under root home directory?

I have tried to create ln -s for this opends directory(as root using "sudo su") under /opt. But not able to create it. Don't know exatcly what is the problem?

ls -s /root/OpenDS-2.0.0 /opt/OpenDS-2.0.0

Bottom line is need to execute this "/root/OpenDS-2.0.0/bin/control-panel" as non root user.

can anybody help it?

Details:
Ubuntu 9.04 \n \l
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"

Thanks in advance.

Regards,
ralus

---

