---
title: "Mount segmentation fault"
date: 2010-08-22
forum: General Help
---

### Post by alex-m on 2010-08-22
Hi! This problem appears to be another case of a "disappeared" partition, in specific, my Windows 7 one.

Here's some terminal output to show you some of the problem:

```
alex@Lapsly:~$ sudo fdisk -l
[sudo] password for alex: 

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1c9ea91d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       22102   175993856    7  HPFS/NTFS
/dev/sda3           23632       24322     5541888   17  Hidden HPFS/NTFS
/dev/sda4           22103       23631    12281662    5  Extended
/dev/sda5           22103       23561    11719386   83  Linux
/dev/sda6           23562       23631      562243+  82  Linux swap / Solaris

Partition table entries are not in disk order
alex@Lapsly:~$ sudo mkdir -p /mnt/tmp
alex@Lapsly:~$ sudo mount /dev/sda2 /mnt/tmp
Segmentation fault

```

sda2 is the Windows partition. After booting into Ubuntu one day, this suddenly happened. Update-grub would no longer recognize the partition or OS, and it was removed from the list. I was able to get back into Win7 by adding a 40_custom entry. I was able to run a chkdsk in Windows after this, but it turned up nothing.

I also noticed that upon booting Ubuntu, this single message appears: (I took a photo, then wrote it down here)

```
udevd-work[99]: `/sbin/blkid -o udev -p /dev/sda2` unexpected exit with status 0x000b
```

If anyone has any ideas as to what's causing this, and perhaps how to fix it, please mention them!

Thanks.

---

