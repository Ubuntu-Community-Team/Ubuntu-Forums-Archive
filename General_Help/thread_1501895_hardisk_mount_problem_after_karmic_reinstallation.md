---
title: "hardisk mount problem after karmic reinstallation"
date: 2010-06-04
forum: General Help
---

### Post by Tiko on 2010-06-04
Hi all,

I recently reinstalled karmic, after upgrading lucid messed up my display.
I did not do a hard disk wipe, but just installed karmic in a new partition.

This presents a problem, which I think is due to permissions, that my other partitions does not mount automatically. Boot up shows a message that there's error.

After looking through the forums, most related issues i see are external devices (I may have missed it). Mine, however, is internal hard drive.

I have to manually mount it in desktop, by password authentication

Here's my fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=5c1919d6-8d8c-4e52-9c50-dd1d582a9421 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=19b4af67-04cf-4027-89a1-ffdd834dd749 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```Hope someone could help me with the 2 weird UUID harddisk :/

I would like to auto-mount it during boot, and perhaps get rid of the weird UUID. 

Many thanks!

---

### Post by Tiko on 2010-06-09
Bump~

Help would be greatly appreciated, please.

---

