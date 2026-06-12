---
title: "Error mounting a hard disc drive using a ubuntu-10.10-i386-in-USB-flash-disc-drive"
date: 2010-12-06
forum: General Help
---

### Post by jmbiscarra on 2010-12-06
I have a portable ubuntu 10.10 i386 -- installed in a USB Flash Disc Drive (USBFDD).

I booted my computer using my USBFDD. The computer I booted has its own Hard Disc Drive, but I cannot access it. I cannot mount it using Disc Utility. When I click the Mount Volume button a notification appears (See attachment).

How do I mount the volume?

---

### Post by Rubi1200 on 2010-12-06
Hi,
from the terminal on the flash drive install, post the output of the following commands please:

```
sudo fdisk -lu

cat /etc/fstab
```

Thanks.

---

### Post by jmbiscarra on 2010-12-06
Hello. I am using a different computer and it still cannot mount the HDD.



For sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x03740374

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   625121279   312560608+   7  HPFS/NTFS

Disk /dev/sdb: 16.0 GB, 16018046976 bytes
255 heads, 63 sectors/track, 1947 cylinders, total 31285248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003fffd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    29878271    14938112   83  Linux
/dev/sdb2        29880318    31283199      701441    5  Extended
/dev/sdb5        29880320    31283199      701440   82  Linux swap / Solaris






For cat /etc/fstab


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=63864832-4aa9-4097-a586-4e1ad8a7c570 none            swap    sw              0       0

---

### Post by ppv on 2010-12-06
mtab may be corrupted. Can you do a ls -l on /etc/mtab....

---

### Post by efflandt on 2010-12-06
Something is strange.  What is the output of **mount**, **df -m**, and **sudo blkid**?  Your sda1 is marked in the partition table as HPFS/NTFS, yet your /etc/fstab shows mounting sda1 ext4 as /.  You should really use UUID's in fstab instead of /dev/sdx#'s.

If you are actually running from ext4 on sda1, and the partition table is mismarked, that might explain why you cannot mount it.  And if you try to connect it to another computer with Windows, Windows would not know how to mount ext4 (even if the partition was correctly marked as Linux).

---

### Post by jmbiscarra on 2010-12-06
Funny I do not have a /etc/mtab/ directory. my mtab is not corrupt. It is MISSING. I don't even have /etc/fstab/. Shame. What should I do?

---

