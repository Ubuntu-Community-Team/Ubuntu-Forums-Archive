---
title: "Basic Raid Question"
date: 2010-01-04
forum: General Help
---

### Post by FiniteRed on 2010-01-04
Happy New year Everyone!

I have discovered that over the holidays my Ubuntu server has dropped a Raid disk (from md3) and now shows it as 'degraded'.

```
administrator@Server:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md3 : active raid1 sdd1[1]
      488383936 blocks [2/1] [_U]
      
md2 : active raid1 sdb3[0] sda3[1]
      67400640 blocks [2/2] [UU]
      
md1 : active raid1 sdb2[0] sda2[1]
      979840 blocks [2/2] [UU]
      
md0 : active raid1 sdb1[0] sda1[1]
      9767424 blocks [2/2] [UU]
      
unused devices: <none>
administrator@Server:~$ sudo mdadm -D /dev/md3
/dev/md3:
        Version : 00.90.03
  Creation Time : Thu Jul 31 15:49:35 2008
     Raid Level : raid1
     Array Size : 488383936 (465.76 GiB 500.11 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 3
    Persistence : Superblock is persistent

    Update Time : Mon Jan  4 11:10:05 2010
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : dc08fdbc:cd25902a:06a14dea:4afc461f (local to host Server)
         Events : 0.236662

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       49        1      active sync   /dev/sdd1
```

I have found some info in the internet on how to re-add the software raid:

mdadm /dev/md3 -a /dev/sdc1

How does this work exactly? Am I in danger of raiding the wrong way round and overwriting and new data on the good (active) disk?

---

