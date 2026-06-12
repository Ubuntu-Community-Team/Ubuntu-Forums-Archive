---
title: "Trying to install Xubuntu as a guest OS in virtualbox"
date: 2010-09-23
forum: General Help
---

### Post by geo909 on 2010-09-23
Hello all,

I followed [this page]("http://forums.virtualbox.org/viewtopic.php?t=15679") to try to install the guest additions to xubuntu 10.4 which I have installed as a virtualbox guest OS, inside ubuntu 9.04. So, I installed
linux-generic-headers, and the build essentials, as advised.

I mounted the additions iso, and then tried to run as superuser the installation file.. This is what I got:

```

jorge@vmachine:/media/VBOXADDITIONS_2.1.4_42893$ sudo sh VBoxLinuxAdditions-x86.run 
Verifying archive integrity... All good.
Uncompressing VirtualBox 2.1.4 Guest Additions for Linux installation...........................................................................................................................................................................................................
VirtualBox 2.1.4 Guest Additions installation
Building the VirtualBox Guest Additions kernel module...
Building the shared folder support kernel module...
Unable to build the kernel module.  See the log file /var/log/vboxadd-install.log
for more details.
jorge@vmachine:/media/VBOXADDITIONS_2.1.4_42893$ 

```

I also attach the log file..

Any ideas?

Many thanks in advance!

---

### Post by yunchiluo on 2010-09-23
Can't seem to read your log. Could you check the tar file?

---

### Post by geo909 on 2010-09-24
Oops!! You're right, there's no log file.. Thanks for the heads up!

I will upload the log file next time I go to school (I'm working in the labs)..

---

### Post by geo909 on 2010-09-24
So, I upload again the tar file with the log file..

Any ideas?

---

