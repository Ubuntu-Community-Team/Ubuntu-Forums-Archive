---
title: "disk removed from raid"
date: 2011-07-25
forum: General Help
---

### Post by zuku on 2011-07-25
hi,
I need your help my status of /dev/md0 looks like this:

mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Thu Dec 17 11:32:43 2009
     Raid Level : raid1
     Array Size : 476503808 (454.43 GiB 487.94 GB)
  Used Dev Size : 476503808 (454.43 GiB 487.94 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Jul 25 10:55:50 2011
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       0        0        1      removed


how to reenable my /dev/sdb1 in this raid, or check it for errors?

---

