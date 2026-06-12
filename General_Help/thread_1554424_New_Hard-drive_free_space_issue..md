---
title: "New Hard-drive free space issue."
date: 2010-08-16
forum: General Help
---

### Post by DJJB on 2010-08-16
I bought a Hitachi Deskstar 1TB hard drive and I am running it on a Dell Vostro 220 with Ubuntu Desktop. When I plugged it in and started up the computer it only shows up as 13.3gb's free space and nothing actually inside the folder. 

Not sure what is up, any help would be much appreciated. Thank you.

By the way this is an additional hard drive on top of my 250gb drive which has the system files on it.

---

### Post by efflandt on 2010-08-17
What size partition(s) did you put on it?

What does **sudo fdisk -l** (small L) show for it?

This is an example of a 1 TB drive on a Dell XPS 8100 that I have not put Linux on yet (running 64-bit 10.04 from USB hd.

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2fb1db22

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1541    12331008    7  HPFS/NTFS
/dev/sda3            1541      121601   964386816    7  HPFS/NTFS
```

---

