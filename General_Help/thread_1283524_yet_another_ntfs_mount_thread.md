---
title: "yet another ntfs mount thread"
date: 2009-10-05
forum: General Help
---

### Post by coze on 2009-10-05
hello guys,
I'm sorry and rather embarrassed to bring up this issue once again, alas there's a situation I can't solve.
I have xubuntu installed on a 32gb ssd drive (via winXP but anyway)
I have two other drives, one has a single ntfs partition and I have no problems accessing it.
the other I have three ntfs partitions, all of them primary partitions.
on the xubuntu side it sees this drive as a SFS file system and sees only the first partition.
how can I mount the other partitions on this drive ?

I'm having problems with sdb, 320 gb drive

> Disk /dev/sda: 32.2 GB, 32296140800 bytes
255 heads, 63 sectors/track, 3926 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1402    11261533+   7  HPFS/NTFS
/dev/sda2            1403        3554    17285940   83  Linux
/dev/sda3            3555        3926     2988090   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x0b93b738

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      620181   312571192+  42  SFS

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
16 heads, 63 sectors/track, 2907021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x87996b82

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1     2907017  1465136536+   7  HPFS/NTFS


---

