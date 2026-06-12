---
title: "(g)parted reports disk unallocated but (s)fdisk shows partitions"
date: 2012-02-02
forum: General Help
---

### Post by curtesy on 2012-02-02
My system is dual boot, XP and Ubuntu 7.1.  Computer works great in both OS's, however, Gparted cannot access any partitions..it shows entire disk is unallocated.  

fdisk does not indicate a problem, sfdisk indicates that some partitions do not start on a proper cylinder boundary?


OUTPUTS from fdisk and sfdisk:
.....................
(fdisk -l)

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x6a796a79 
 Device  Boot  Start  End    Blocks   Id  System
/dev/hda1 *       1  1483   11912166    7  HPFS/NTFS
/dev/hda2      5100  9565   35873145   83  Linux
/dev/hda3      1484  9729   66235993+   f  W95 Ext'd (LBA)
/dev/hda5      1484  3340   14916319+   7  HPFS/NTFS
/dev/hda6      9684   9729    369463+  82  Linux swap /Solaris

.....................................

(sfdisk -l)

Disk /dev/hda: 9729 cylinders, 255 heads, 63 sectors/track

Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0
   
Device   Boot Start  End   #cyls  #blocks   Id  System
/dev/hda1 *   0+   1482   1483-  11912166    7  HPFS/NTFS
/dev/hda2  5099    9564   4466   35873145   83  Linux
      start: (c,h,s) expected 1023,254,63) found (1023,0,1)
/dev/hda3  1483+   9728   8246-  66235993+   f  W95 Ext'd (LBA)
      start: (c,h,s) expected 1023,254,63) found (1023,0,4)
/dev/hda4     0       -       0          0    0  Empty
/dev/hda5  1483+   3339    1857-  14916319+   7  HPFS/NTFS
      start: (c,h,s) expected 1023,254,63) found (1023,1,1)
/dev/hda6  9683+   9728      46-    369463+  82  Linux swap / Solaris
      start: (c,h,s) expected 1023,254,63) found (1023,1,1)

Partition table entries are not in disk order

...............................


fdisk seems to say that all is ok, however, sfdisk says that there are some parts that are not correct as shown above.

How can I fix the partitions so that gparted sees the disk correctly?

Curt

---

### Post by lechien73 on 2012-02-02
It looks like hda2 and hda3 are overlapping partitions, which would cause GParted to fail.

You could try running TestDisk ([http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)), which should be able to repair the partition table.

Make sure you have a backup of data before attempting any change to the partition tables though!!

---

### Post by varunendra on 2012-02-04
> **curtesy said:**
> My system is dual boot, XP and Ubuntu 7.1.

Is there some specific reason why you are using such an old version of Ubuntu?

I second *lechien73's* suggestion to backup your data then try testdisk, but I also suggest to try a live cd of a [newer version of Ubuntu]("http://www.ubuntu.com/download/ubuntu/download") (e.g. default 10.04.3 LTS or 11.10 - if [systems specs]("https://help.ubuntu.com/community/Installation/SystemRequirements") are good enough, or [Xubuntu]("http://xubuntu.org/getxubuntu/") 10.04.3 LTS or 11.10 if the specs are low). If any of these seem to run smooth on your computer, just install them removing the current one. They provide a newer version of gparted, which is more capable in handling partitions if further troubleshooting or partition manipulation is required.

---

