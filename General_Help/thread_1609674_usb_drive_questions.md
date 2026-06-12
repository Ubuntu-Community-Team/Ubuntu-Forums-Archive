---
title: "usb drive questions"
date: 2010-10-30
forum: General Help
---

### Post by strider22 on 2010-10-30
How do you find out which UCB device in lsusb maps to what /dev entry?

How do you find out which /dev entry maps to what /device entry?

What about drives with multiple partitions?

---

### Post by C.S.Cameron on 2010-10-31
If you are using Ubuntu open gparted.

---

### Post by Verbeck on 2010-10-31
while connected, type **sudo blkid -c /dev/null** in a terminal or open system>administration>disk utility

---

### Post by inameiname on 2010-10-31
Gparted or Disc Utility is probably the easiest.

Personally, I use Gparted for formatting, and Disc Utility for checking the drive locale and mounting and unmounting whenever desired. With it, I can look, and not have to worry about hitting a button and accidentally screwing something up if I'm not paying attention in Gparted. Just personal choice for such.

---

### Post by HermanAB on 2010-10-31
Howdy,

Removable media will mount in a predictable way under /media if you give the filesystem a proper Label.

You can also use the UID to mount a device.

---

### Post by strider22 on 2010-10-31
Thanks. blkid was useful. It led me to ls /dev/disk/by-UUID and hence to;

 ls /dev/disk/by-id     (Only the usb part)
usb-ST310005_28AS_630FFFFFFFFF-0:0
usb-ST310005_28AS_630FFFFFFFFF-0:0-part1
usb-ST332062_0A_DEF10AF1F9AD-0:0
usb-ST332062_0A_DEF10AF1F9AD-0:0-part1
usb-ST332062_0A_DEF10AF1F9AD-0:0-part2
usb-ST332062_0A_DEF10AF1F9AD-0:0-part5
usb-WD_3200AAJ_External_57442D574D41543132303931383532-0:0
usb-WD_3200AAJ_External_57442D574D41543132303931383532-0:0-part1

This provides me with easy access to the drive manufacturer and model. It also shows the partitions there. (note 2 different seagate drives: ST31 & ST33) The second drive (ST33) has 2 primary partitions. The second primary partition has one extended partition. We only mount the extended partition.


How do I query the HAL or hardware abstraction layer to see which device is mounted by each /media mount point?

---

### Post by strider22 on 2010-10-31
Adding dash L to the above command connects the drive manufacturer to the /dev entry

$ ls -l /dev/disk/by-id/
lrwxrwxrwx 1 root root  9 2010-10-30 16:10 usb-ST310005_28AS_630FFFFFFFFF-0:0 -> ../../sdc
lrwxrwxrwx 1 root root 10 2010-10-30 16:10 usb-ST310005_28AS_630FFFFFFFFF-0:0-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 2010-10-30 16:27 usb-ST332062_0A_DEF10AF1F9AD-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 2010-10-30 16:27 usb-ST332062_0A_DEF10AF1F9AD-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2010-10-30 16:27 usb-ST332062_0A_DEF10AF1F9AD-0:0-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 2010-10-30 16:27 usb-ST332062_0A_DEF10AF1F9AD-0:0-part5 -> ../../sdb5
lrwxrwxrwx 1 root root  9 2010-10-30 15:40 usb-WD_3200AAJ_External_57442D574D41543132303931383532-0:0 -> ../../sdd
lrwxrwxrwx 1 root root 10 2010-10-30 15:40 usb-WD_3200AAJ_External_57442D574D41543132303931383532-0:0-part1 -> ../../sdd1

---

### Post by strider22 on 2010-10-31
And this connects the /dev entry to the label used in /media and which shows up in Nautilus. If there is no label then the drive does not show up here.
blkid is probably easier to read.

$ ls -l /dev/disk/by-label/
total 0
lrwxrwxrwx 1 root root 10 2010-10-30 11:25 HDDRECOVERY -> ../../sda3
lrwxrwxrwx 1 root root 10 2010-10-30 16:10 Iomega\x20HDD -> ../../sdc1
lrwxrwxrwx 1 root root 10 2010-10-30 15:40 My\x20Book -> ../../sdd1
lrwxrwxrwx 1 root root 10 2010-10-30 16:27 New\x20Volume -> ../../sdb5
lrwxrwxrwx 1 root root 10 2010-10-30 11:25 S3A6134D002 -> ../../sda2
lrwxrwxrwx 1 root root 10 2010-10-30 11:25 TOSHIBA\x20SYSTEM\x20VOLUME -> ../../sda1

---

### Post by mikewhatever on 2010-10-31
Take a look at 'man udisks'. I think something like 
```
udisks --show-info [device/partition]
```
will show the same or more info.

---

