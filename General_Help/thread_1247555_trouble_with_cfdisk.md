---
title: "trouble with cfdisk"
date: 2009-08-23
forum: General Help
---

### Post by nikhilbhardwaj on 2009-08-23
here's what i get when i run

sudo cfdisk /dev/sdb

FATAL ERROR: Bad primary partition 2: Partition ends in the final partial cylinder
                          Press any key to exit cfdisk

here's an output of my fdisk -l
```

[nikhil@localhost PCMagazine]$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40059321856 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00006a32                     

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         158     1269103+  82  Linux swap / Solaris
/dev/sda2             159        1223     8554612+  83  Linux
/dev/sda3            1224        4870    29294527+   5  Extended
/dev/sda5            1224        4870    29294496    b  W95 FAT32
omitting empty partition (5)

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcf87cf87

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1979    15896286    7  HPFS/NTFS
/dev/sdb2            1980       19436   140223289+   f  W95 Ext'd (LBA)
/dev/sdb3           19437       19458      171233+  83  Linux
/dev/sdb5            1981        3285    10482381   83  Linux
/dev/sdb6            3286       14111    86959813+   b  W95 FAT32
/dev/sdb7           14112       19436    42773031    b  W95 FAT3

```

i can mount and use them but why doesn't cfdisk recognize the partitions

---

### Post by BitJunkie on 2009-09-09
I have a very similar problem. Have you found a solution yet?

---

### Post by nikhilbhardwaj on 2009-10-10
> **BitJunkie said:**
> I have a very similar problem. Have you found a solution yet?

nope 

but i guess htat it is because i used paragon partition manager to resize a partition from within windows

---

