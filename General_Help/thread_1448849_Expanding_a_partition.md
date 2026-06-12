---
title: "Expanding a partition"
date: 2010-04-07
forum: General Help
---

### Post by glennbtn on 2010-04-07
Hi All

Still new to Ubuntu and need a little help. I have a vmware of Ubuntu 8.04 along with Zimbra. I had been running out of space so gave the vmware disk space more room. What I need to know now is how I expand sda1 to give it the extra space allocated.

This is the current setup although the new free space does not show anywhere

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         993     7976241   83  Linux
/dev/sda2             994        1044      409657+   5  Extended
/dev/sda5             994        1044      409626   82  Linux swap / Solaris

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext3    7.6G  5.2G  2.0G  73% /
varrun       tmpfs    377M   44K  377M   1% /var/run
varlock      tmpfs    377M     0  377M   0% /var/lock
udev         tmpfs    377M   44K  377M   1% /dev
devshm       tmpfs    377M     0  377M   0% /dev/shm

Thanks

---

### Post by syncmasterpt on 2010-04-07
Follow this steps:

 1) Stop your virtual machine and backup it
 2) Download the gparted iso
 3) Make your virtual machine to boot from the gparted iso, namely by defining it as a CDROM and when booting choosing to boot from cd
 4) After booting into gparted you can increase and move your partitions
 5) Save the changes, and before rebooting, remove the ISO from the CDrom

Hope this helps!

---

### Post by glennbtn on 2010-04-07
Worked perfectly. Thanks

---

### Post by syncmasterpt on 2010-04-07
Great!

---

