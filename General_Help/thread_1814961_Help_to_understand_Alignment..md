---
title: "Help to understand Alignment."
date: 2011-07-30
forum: General Help
---

### Post by MinDokan on 2011-07-30
Help to understand disk Alignment.
I've recently installed Ubuntu alongside Windows 7.
I created 4 logical partitions: /boot, swap, / and /home. In that order.
I've noticed no lag nor system hang.

Disk Utility, show a warning. See     [disk1.png]("http://ubuntuforums.org/attachment.php?attachmentid=198861&stc=1&d=1312040989")     (87.0 KB).

Then fdisk -l report.
```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x8e24bc24

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       26833   215428096    7  HPFS/NTFS
/dev/sda3           26833       77826   409597953    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5           26833       26869      291840   83  Linux
/dev/sda6           26870       27113     1951744   82  Linux swap / Solaris
/dev/sda7           27113       28328     9764864   83  Linux
/dev/sda8           28328       77826   397586432   83  Linux

Disk /dev/dm-0: 1998 MB, 1998585856 bytes
255 heads, 63 sectors/track, 242 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd655d407

```I think I have a problem, but, do I have to worry about?
I hope someone help me to understand the fdisk report.

Thanks in advance.

MinDokan.

---

