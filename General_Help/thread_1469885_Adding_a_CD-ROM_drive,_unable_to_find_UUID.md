---
title: "Adding a CD-ROM drive, unable to find UUID"
date: 2010-05-02
forum: General Help
---

### Post by thecapsaicinkid on 2010-05-02
Hi all,

Just added a DVD drive to a machine which had no drive before. When I boot I get the error about being unable to find the root drive by its UUID. If I unplug the DVD drive it boots as normal.

I'm guessing the root drive is getting a new name i.e /dev/sda2 instead of sda1 and thus a new UUID. How can I add the drive and fix the UUID issue in grub?


Many thanks

---

### Post by thecapsaicinkid on 2010-05-08
Any ideas?

The busybox shell I'm dropped to doesn't have access to commands like update-grub etc


Thanks

---

### Post by dcstar on 2010-05-08
> **thecapsaicinkid said:**
> Hi all,

Just added a DVD drive to a machine which had no drive before. When I boot I get the error about being unable to find the root drive by its UUID. If I unplug the DVD drive it boots as normal.

I'm guessing the root drive is getting a new name i.e /dev/sda2 instead of sda1 and thus a new UUID. How can I add the drive and fix the UUID issue in grub?


Many thanks

Post your /etc/fstab file.

---

### Post by chappajar on 2010-05-09
sudo blkid 

will list your uuids.

---

### Post by thecapsaicinkid on 2010-05-09
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=afad86fc-3229-4dbe-9d44-21f4100e9eff /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=4386455e-3ece-4b44-8e58-d53bfc10892a /myth           ext3    relatime        0       2
# /dev/sda2
UUID=a5db98ae-4590-476c-b21a-831b46037550 none            swap    sw              0       0
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

This cd drive used to be installed in this machine a while back, tried commenting it out but no luck. The drive with UUID ending in 9eff is the root drive which it complains it cannot find.


I cannot run blkid from the shell provided when the machine doesn't boot with the drive attached. Will I need a live cd to fix this issue?

---

### Post by thecapsaicinkid on 2010-05-16
Any ideas?

---

### Post by thecapsaicinkid on 2010-05-17
Bump

---

### Post by thecapsaicinkid on 2010-05-18
Fix was here

[http://newyork.ubuntuforums.org/showpost.php?p=8915160&postcount=3](http://newyork.ubuntuforums.org/showpost.php?p=8915160&postcount=3)


..but with rootdelay=120 and not 60


Why am I having to do this because I've added a CD-ROM drive? The machine takes ages to boot now.

---

### Post by izz.y on 2010-05-18
I know they removed the hardware abstraction layer in booting Ubuntu 10.04. I am fairly new to Linux, but I think that is what is causing your problems.

---

