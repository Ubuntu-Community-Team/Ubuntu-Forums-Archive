---
title: "Please Help Me Identify These Partitions"
date: 2011-07-01
forum: General Help
---

### Post by umechanism on 2011-07-01
I have upgraded Ubuntu several times over the years but this time I want to blow away everything and start new.  I am dual-booting with Windows so I don't want to touch the Windows partitions.  I only want to erase the Linux partitions so I can install a fresh copy of Ubuntu 11.04.  Here are my partitions:
```
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2              10        1968    15728640    7  HPFS/NTFS
/dev/sda3   *        1968       46317   356239958+   7  HPFS/NTFS
/dev/sda4           46318       91201   360530730    5  Extended
/dev/sda5           46318       89971   350650723+  83  Linux
/dev/sda6           89972       91201     9879943+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c529c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS

```

Seems to be I can delete sda4 through sda6 then reinstall Ubuntu there.  Correct?

---

### Post by collisionystm on 2011-07-01
> **umechanism said:**
> I have upgraded Ubuntu several times over the years but this time I want to blow away everything and start new.  I am dual-booting with Windows so I don't want to touch the Windows partitions.  I only want to erase the Linux partitions so I can install a fresh copy of Ubuntu 11.04.  Here are my partitions:
```
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2              10        1968    15728640    7  HPFS/NTFS
/dev/sda3   *        1968       46317   356239958+   7  HPFS/NTFS
/dev/sda4           46318       91201   360530730    5  Extended
/dev/sda5           46318       89971   350650723+  83  Linux
/dev/sda6           89972       91201     9879943+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c529c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS

```Seems to be I can delete sda4 through sda6 then reinstall Ubuntu there.  Correct?

Or you can just pop in the 11.04 install disk, and choose to erase linux only

---

### Post by jerome1232 on 2011-07-01
sda4 is just an extended partition which holds logical partitions, let it be, just overwrite sda5 and sda6

---

### Post by umechanism on 2011-07-01
Got it.  Thanks for the help.

---

