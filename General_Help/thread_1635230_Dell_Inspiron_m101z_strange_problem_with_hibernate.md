---
title: "Dell Inspiron m101z strange problem with hibernate and swap file"
date: 2010-12-01
forum: General Help
---

### Post by Dr.Fuzzy on 2010-12-01
I have a Dell m101z laptop in dual boot configuration running Ubuntu 10.10 + W7. The hibernate and suspend option worked like a charm until I proceeded with some updates a few days ago from the update manager. After that  the hibernate button mysteriously disappeared! Then I tried to install uswsusp (s2ram and s2disk) and to my surprise it reports that my swap file is invalid and fails to install! 

my fdisk -l

```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x83fc49c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           5       40129+   6  FAT16
Partition 1 does not end on cylinder boundary.
/dev/sda2               6        1918    15360000    7  HPFS/NTFS
/dev/sda3            1918       12246    82963073+   7  HPFS/NTFS
/dev/sda4           12246       30402   145840023    f  W95 Ext'd (LBA)
/dev/sda5           12246       29659   139870208   83  Linux
/dev/sda6           29659       30402     5962744   82  Linux swap / Solaris

```

Any ideas???

---

### Post by Dr.Fuzzy on 2010-12-02
Anyone...?

---

### Post by erlguta on 2011-02-22
Read all this post:
[http://ubuntuforums.org/showthread.php?t=1546920](http://ubuntuforums.org/showthread.php?t=1546920)

---

