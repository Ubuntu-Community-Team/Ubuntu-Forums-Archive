---
title: "MD raid5 degradation - 12.4 LTS"
date: 2012-07-17
forum: General Help
---

### Post by mcc666 on 2012-07-17
Hello,

   i've installed ubuntu 12.4 migrating from kubuntu (the same version). I installed all from the begining, just left md raid and lvm on top as it was. All went ok, and i was using ubuntu for quite a while. Just day ago when i was trying to boot my pc i got information that the md is corrupted - only 2 out of 3 disks are available. 

Pls see the info:
```
cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid5 sdb2[0] sdc2[1]
      974213504 blocks level 5, 64k chunk, algorithm 2 [3/2] [UU_]
      
unused devices: <none>

```

My disks in raid5 were sdb2, sdc2, sdh2. What i see now is:

```

sudo mdadm --examine /dev/sdc2
/dev/sdc2:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 9766fef5:dea82019:8cff746d:cc9f262c
  Creation Time : Sat Mar 15 23:22:52 2008
     Raid Level : raid5
  Used Dev Size : 487106752 (464.54 GiB 498.80 GB)
     Array Size : 974213504 (929.08 GiB 997.59 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 1

    Update Time : Tue Jul 17 17:23:50 2012
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 2e182e2d - correct
         Events : 2741763

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       34        1      active sync   /dev/sdc2

   0     0       8       18        0      active sync   /dev/sdb2
   1     1       8       34        1      active sync   /dev/sdc2
   2     2       0        0        2      faulty removed


```

```

 sudo mdadm --examine /dev/sdb2
/dev/sdb2:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 9766fef5:dea82019:8cff746d:cc9f262c
  Creation Time : Sat Mar 15 23:22:52 2008
     Raid Level : raid5
  Used Dev Size : 487106752 (464.54 GiB 498.80 GB)
     Array Size : 974213504 (929.08 GiB 997.59 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 1

    Update Time : Tue Jul 17 17:24:44 2012
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 2e182ea5 - correct
         Events : 2741805
         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       18        0      active sync   /dev/sdb2

   0     0       8       18        0      active sync   /dev/sdb2
   1     1       8       34        1      active sync   /dev/sdc2
   2     2       0        0        2      faulty removed


```

BUT:confused::

```

sudo mdadm --examine /dev/sdh2
/dev/sdh2:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 9766fef5:dea82019:8cff746d:cc9f262c
  Creation Time : Sat Mar 15 23:22:52 2008
     Raid Level : raid5
  Used Dev Size : 487106752 (464.54 GiB 498.80 GB)
     Array Size : 974213504 (929.08 GiB 997.59 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1

    Update Time : Mon Jul 16 12:24:39 2012
          State : active
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 2decb533 - correct
         Events : 2738529

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8      114        2      active sync   /dev/sdh2

   0     0       8       82        0      active sync
   1     1       8       98        1      active sync
   2     2       8      114        2      active sync   /dev/sdh2


```

I was trying to make sdh2 inactive but i can't do that:

```

sudo mdadm --manage --set-faulty /dev/md1 /dev/sdh2 
mdadm: set device faulty failed for /dev/sdh2:  No such device

```

Can anyone help me with getting back to fully operational state please? I've checked and windows sees this disc, but i can't see it under ubuntu.

What do you propose? Removing all partitions and rebuild all? I don't want to lose TB of data...

Thx in advance!

BR,
MCC

---

### Post by mcc666 on 2012-07-18
I am responding to myself :) Something has happen with consistency of block on last disc. 

So I run live USB system and:

```

sudo mdadm --zero-superblock /dev/sdX2

```

```

sudo mdadm --manage /dev/md1 --add /dev/sdX2

```

Now I'll be waiting a few hrs and checking:

```

cat /proc/mdstat

```

BR,
MCC

---

