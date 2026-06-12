---
title: "Windows doesn't immediately boot after using Ubuntu"
date: 2010-05-04
forum: General Help
---

### Post by Ayukawa on 2010-05-04
I have a dual boot setup with two hard drives.  Windows 7 is running on my primary drive with Ubuntu 10.04 on the secondary drive.  I installed GRUB 2 to the secondary hard drive, and I'm booting from that.

Everything seems to be working well with one problem.  Every time I shut down from Ubuntu and tell it to load Windows (it doesn't matter if it's a reboot or power off/on), Windows locks up during its boot.  

If I power the laptop off and back on, I can select and load into Windows just fine.  It just takes two attempts EVERY time.

---

### Post by SnickerSnack on 2010-05-04
Can you post the output of

```
sudo fdisk -l
```

?

I've found that windows is very picky, and you really should be booting from the partition that windows is on.  I think that means you'll have grub installed there.

---

### Post by Ayukawa on 2010-05-04
Disk /dev/sda: 320.1 GB, 320072933376 bytes
4 heads, 44 sectors/track, 3551945 cylinders
Units = cylinders of 176 * 512 = 90112 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x97646c29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      127973    11261592+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *      127977      129141      102400    7  HPFS/NTFS
/dev/sda3          129141     3551931   301205504    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00053e43

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18663   149903360   83  Linux
/dev/sdb2           18663       19458     6384641    5  Extended
/dev/sdb5           18663       19458     6384640   82  Linux swap / Solaris

---

