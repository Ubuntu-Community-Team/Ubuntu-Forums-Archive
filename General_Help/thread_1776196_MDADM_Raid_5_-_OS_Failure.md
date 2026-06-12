---
title: "MDADM Raid 5 - OS Failure"
date: 2011-06-05
forum: General Help
---

### Post by Wazz72 on 2011-06-05
I have 4 WD10EARS drives running in a RAID 5 array using MDADM.
Yesterday my OS Drive failed.  I have replaced this and installed a fresh copy of Ubuntu 11.04 on it.
I then installed MDADM, and rebooted the machine, hoping that it would automatically rebuild the array.
It hasnt, when i look at the array using Disk Utility, it says that the array is not running.  If i try to start the array it says : 

Error assembling array: mdadm exited with exit code 1: mdadm: failed to RUN_ARRAY /dev/md0: Input/output error
mdadm: Not enough devices to start the array.

I have tried MDADM --assemble --scan and it gives this output:

mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.

I know that there are 4 drives present as they are all showing, but it is only using 2 of them.

I also ran MDADM -- detail /dev.md0   which gave:


root@warren-P5K-E:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Tue Dec 21 20:00:42 2010
     Raid Level : raid5
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
   Raid Devices : 4
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Jun  2 08:27:09 2011
          State : active, FAILED, Not Started
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 78bded27:4f36b420:b8c93aaa:68704163
         Events : 0.61

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       32        1      active sync   /dev/sdc
       2       0        0        2      removed
       3       8       48        3      active sync   /dev/sdd


By looking at this it looks like only 2 of th 4 drives are activated.

How do I get them all active and start the array again.

There has been nothing written to any of the 4 drives.

Any help would be appreciated.

---

### Post by Wazz72 on 2011-06-06
Just did a :
mdadm --assemble --scan -v

and it returned :

mdadm: /dev/sdb is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sdd is identified as a member of /dev/md0, slot 3.
mdadm: /dev/sdc is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sda is identified as a member of /dev/md0, slot 0.
mdadm: added /dev/sda to /dev/md0 as 0
mdadm: added /dev/sdb to /dev/md0 as 2
mdadm: added /dev/sdd to /dev/md0 as 3
mdadm: added /dev/sdc to /dev/md0 as 1
mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.

does this mean disks 2 & 4 are in the wrong order?

---

### Post by Wazz72 on 2011-06-06
I could really do with some help here,  please.

---

