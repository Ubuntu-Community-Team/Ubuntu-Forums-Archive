---
title: "Ubuntu 8.10 64Bit server boots into busybox (initramfs) HELP!!"
date: 2009-12-09
forum: General Help
---

### Post by DarwinLabs on 2009-12-09
I am having issues booting my ubuntu server box.
it starts up like so
{Beginning}
Starting up ...
loading please wait...
19+0 records in
19+0 records out
kinit: name_to_dev_t(dev/md2) = dev(9,2)
kinit: trying to resume from /dev/md2
kinit: No resume image, doing normal boot...
mount: mounting /root/dev on /dev./static/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
Target filesystem doesn't have /sbin/init.
no init found. Try passing init= bootarg.


BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of commands.

(initramfs)
{End}

all I have done is rebooted the box. my setup is like so
2 80GB IDE drives for OS
sda1, sdb1 -> md0 = 100MB  /boot
sda2, sdb2 -> md1 = 71GB   /
sda3, sdb3 -> md2 = 8GB    SWAP

Please help I need this up and running and I'm still kinda learning linux.

---

