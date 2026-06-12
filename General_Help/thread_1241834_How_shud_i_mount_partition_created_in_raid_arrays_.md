---
title: "How shud i mount partition created in raid arrays?? it is recognised by dmraid"
date: 2009-08-16
forum: General Help
---

### Post by haider_up32 on 2009-08-16
-using intel matrix manager raid0
-installed ubuntu on non-raid disk
-raid array recognised as separate disk



```
root@mhk-desktop:/home/mhk# sudo dmraid -ay
RAID set "isw_feacijab_Volume0" already active
RAID set "isw_feacijab_Volume01" already active
RAID set "isw_feacijab_Volume02" already active

root@mhk-desktop:/home/mhk# sudo fdisk /dev/mapper/isw_feacijab_Volume0

The number of cylinders for this disk is set to 121602.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p 

Disk /dev/mapper/isw_feacijab_Volume0: 1000.2 GB, 1000210694144 bytes
255 heads, 63 sectors/track, 121602 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb36a5ff6

                            Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_feacijab_Volume0p1   *           1         893     7172991    7  HPFS/NTFS
/dev/mapper/isw_feacijab_Volume0p2             894        1786     7173022+   7  HPFS/NTFS

Command (m for help): 


root@mhk-desktop:/home/mhk# dmraid -s
*** Group superset isw_feacijab
--> Active Subset
name   : isw_feacijab_Volume0
size   : 1953536512
stride : 256
type   : stripe
status : ok
subsets: 0
devs   : 2
spares : 0
```

---

