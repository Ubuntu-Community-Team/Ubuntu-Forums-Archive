---
title: "Restoring Partition Table"
date: 2010-09-13
forum: General Help
---

### Post by cantdrive55 on 2010-09-13
So I was moving around some partitions using gparted and in doing so, it broke both grub and the windows 7 bootloader. somehow i ended up with my drive saying it was unallocated. well i've gotten back my partition table all except for my linux primary partition which holds all my music/movies/pics

i've recovered it back to this point so far.

here's my fdisk -l output:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6b5d8ad1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   280286054   140142996   83  Linux
/dev/sda2       280286055   322215704    20964825    7  HPFS/NTFS
/dev/sda3   *   322215705   364161419    20972857+   7  HPFS/NTFS
/dev/sda4       364161420   625137344   130487962+   f  W95 Ext'd (LBA)
/dev/sda5       364161483   621988604   128913561    7  HPFS/NTFS
/dev/sda6       621988668   625137344     1574338+  82  Linux swap / Solaris
```

however, i can't mount sda1. i know it is an ext4 partition but even when i run parted /dev/sda print it just shows sda1 as having no filesystem.

is there some way for me to force a flag saying its ext4 at least so i can transfer files?

---

### Post by bodhi.zazen on 2010-09-14
Try testdisk

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Should be run from a live CD (testdisk is in the ubuntu repositories).

---

### Post by cantdrive55 on 2010-09-16
After alot of fooling around I was finally able to get the partition table back using testdisk to find delete my partition table and recreate all but the ext4 partition, then I manually added it using fdisk, and finally using fsck and [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/) to restore my superblock, I was able to get back all my data except for a few non-important files.

---

### Post by bodhi.zazen on 2010-09-16
> **cantdrive55 said:**
> I was able to get back all my data except for a few non-important files.

w00t =)

That is most important, glad you were able to recover most of your files / data.

---

