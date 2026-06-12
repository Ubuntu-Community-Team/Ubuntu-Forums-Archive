---
title: "Ubuntu studio Start up fails"
date: 2009-09-05
forum: General Help
---

### Post by marko_1234 on 2009-09-05
Hi,

I've had Ubuntu Studio on my laptop for couple of months and everything was okay until today:

I rebooted and restarting Ubuntu failed as follows:

-------------

Grub seems to work ok and I see glimpse of Ubutun studio logo and then:

Starting up...
Loading, please wait...
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/b7... (lond line)
kinit: trying to resume from... (long line)
mount: mounting /dev/disk/... ... on root failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
No init found. Try passing inti=bootarg.

... and there is a BusyBox build-in shell running.

------------


Could somebody tell me what happened and is there any way to recover the OS
without losing data on hard disk? The laptop is pretty old so a hardware failure is 
also possible..


Cheers!

---

