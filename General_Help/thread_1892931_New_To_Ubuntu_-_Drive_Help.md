---
title: "New To Ubuntu - Drive Help"
date: 2011-12-09
forum: General Help
---

### Post by TheSpastic on 2011-12-09
Hi, Im new to ubuntu and recently installed it to a second drive, but seemingly it has installed on both drives and wiped my windows install (To which i have no disk, anybody know of a way to recover windows without disk, key or install? :S)

Anyway, I can see the partition i created for linux, but I cannot get access through the home folder to my other drive, Using fdisk -l I get:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002b612

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     2930687     1464320   82  Linux swap / Solaris
/dev/sda2         2930688   393555967   195312640   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002b612

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048     2930687     1464320   82  Linux swap / Solaris
/dev/sdb2         2930688   393555967   195312640   83  Linux
```


I'm assuming this si showing me both drives, one drive being sda the other being sdb, with the number being partitions. However, they appear to be set out exactly the same, so maybe this is a bug of some sort and windows is hiding ?

Anyway, One way or the other I do wish to have windows back, unless I can run battlefield 3 directly from linux?

Also, how do I get my second drive to show up in linux? I know it works fine and is connected properly.

Thanks - A ubuntu newbie :) :guitar:

---

