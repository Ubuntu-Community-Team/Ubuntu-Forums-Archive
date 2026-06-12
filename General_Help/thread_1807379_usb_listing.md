---
title: "usb listing"
date: 2011-07-19
forum: General Help
---

### Post by ub007 on 2011-07-19
Hi 

I've plugged a usb stick into my server.

> cat /proc/partitions

   8     0      1981440 sda
   8     1      990720 sda1
   8     2      436288 sda2
However when I do 

> ls /dev/sd*

/dev/sda
/dev/sda1
/dev/sda2
/dev/sdb
/dev/sdb1
/dev/sda2
I'm sure I got no other devices connected that /dev/sd**b** would point to

> cd /sys/block/sda

[root@footy sda]# ll
lrwxrwxrwx 1 root root    0 Jul 18 16:27 device -> ../../devices/pci0000:00/0000:00:03.2/usb1/1-1/1-1:1.0/host0/target0:0:0/0:0:0:0


[root@footy sda]# cd /sys/block/sdb
[root@footy sdb]# ll
lrwxrwxrwx 1 root root    0 Jul 18 16:27 device -> ../../devices/pci0000:00/0000:00:03.2/usb1/1-1/1-1:1.0/host0/target0:0:0/0:0:0:1

What does this imply, sdb linked to sda?

Thanks in advance
David

---

