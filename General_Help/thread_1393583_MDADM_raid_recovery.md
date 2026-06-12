---
title: "MDADM raid recovery"
date: 2010-01-29
forum: General Help
---

### Post by huggy77 on 2010-01-29
i came into my clients office and his hardware raid broke,  i am trying to reassemble it..  I will post my questons now and again at the end.
**Q:1 What do you think is wrong with sdb1**
**Q:2 Will reassembling lose my data?**

**tried** 
```

root@skunkworks:/dev# mdadm --assemble /dev/md0 /dev/sda1 /dev/sdc1 /dev/sdd1 /dev/sdb1

```
> 
mdadm: no RAID superblock on /dev/sdb1
mdadm: /dev/sdb1 has no superblock - assembly aborted

**did:**
```
mdadm --assemble --force /dev/md0 /dev/sda1 /dev/sdc1
```
> 
mdadm: forcing event count in /dev/sda1(0) from 26098 upto 26100
mdadm: /dev/md0 has been started with 2 drives (out of 3).
**was able to add sdd1**
```
root@skunkworks:/dev# mdadm --re-add /dev/md0 /dev/sdd1
```
> mdadm: added /dev/sdd1
**Could not add sdb1:**
```
root@skunkworks:/dev# mdadm --re-add /dev/md0 /dev/sdb1
```
> mdadm: add new device failed for /dev/sdb1 as 3: Invalid argument
**looking at it**
```
root@skunkworks:/dev# mdadm -D /dev/md0
```
> 
/dev/md0:
        Version : 00.90.03
  Creation Time : Fri Oct 19 10:45:12 2007
     Raid Level : raid5
     Array Size : 1465143808 (1397.27 GiB 1500.31 GB)
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Jan 29 12:54:43 2010
          State : clean, degraded, recovering
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 0% complete

           UUID : 88326e8c:2dfd3334:3a6c54f1:4d462123
         Events : 0.26106

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       3       8       49        1      spare rebuilding   /dev/sdd1
       2       8       33        2      active sync   /dev/sdc1

**Looking at the bad disc sdb1**
```
root@skunkworks:/dev# mdadm -E /dev/sdb1
```
> mdadm: No md superblock detected on /dev/sdb1.
**Q:1 What do you think is wrong with sdb1**
**Q:2 Will reassembling lose my data?**

---

### Post by huggy77 on 2010-02-02
any input?  I will find out more tomorrow, stopping at the clients...

---

