---
title: "Start up question"
date: 2010-10-03
forum: General Help
---

### Post by thebigob on 2010-10-03
Ok so I did something really dumb.

I deleted my swap partition by accident.

Ok no problem got this back and fixed ok... or so I though.

I can start up my older kernel no problem however the newest one wont boot. It just hangs at splash.

Interestingly when I boot with splash and quiet switched off it boots fine?

Anyone got any ideas? Is there anything I can provide that will help debug this issue?

---

### Post by Rubi1200 on 2010-10-03
Check your fstab file; you probably need to enter the UUID for the new swap partition.

To find the UUID:

```
sudo blkid
```To edit the swap file:

```
sudo gedit /etc/fstab
```Find the line which says "swap was on...and enter the correct UUID.

The fstab file looks like this (yours will be different of course):
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=7e07a924-8356-48d2-a8ec-65bc85589b04 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c93d7e99-e7f1-4a9d-9b09-94235e14921c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```Save and reboot.

---

