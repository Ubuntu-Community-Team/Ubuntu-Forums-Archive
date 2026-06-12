---
title: "Partitions not detected by ubuntu 9.10."
date: 2010-01-17
forum: General Help
---

### Post by rick_2047 on 2010-01-17
I installed ubuntu 9.10 using the alternate CD but now it does not show two of my 3 partitions. My fdisk -l looks like this
```

/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        4870    28876837+   f  W95 Ext'd (LBA)
/dev/sda5            1276        2103     6650847   83  Linux
/dev/sda6            2104        2459     2859538+   b  W95 FAT32
/dev/sda7            2460        2550      730926   82  Linux swap / Solaris
/dev/sda8            2551        4870    18635368+   b  W95 FAT32

```

out of sda1 ,sda6 and sda8 only sda8 is shown :( . 

I tried the disk utility but, sda1 and sda6 is recognized as unpartitioned space.

Can you please help me?

---

