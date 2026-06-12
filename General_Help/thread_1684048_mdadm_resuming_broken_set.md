---
title: "mdadm resuming broken set"
date: 2011-02-08
forum: General Help
---

### Post by dinomight on 2011-02-08
So i am having trouble resuming an array. When i try it tells me that it's unable to do so because only one drive is available. Here is the weird bit, if i examine each of the drives one thinks that both drives are available and the other drive shows the first drive as being removed. (see below). This is a raid 5 and one of the drive has failed and been removed. I know that this was a terrible idea but the array has been functioning for a few weeks with just the two drives. And now i can't resume. Here is the output of the examine functions for each drive: notice that sda1 sees both drive 0 and 1 as active, but sdb2 sees drive 0 as removed.```


~# mdadm --examine /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : ddf5dbf5:499deb25:19ffd938:6715fbff (local to host localname)
  Creation Time : Fri Jun  1 23:34:11 2007
     Raid Level : raid5
  Used Dev Size : 390708736 (372.61 GiB 400.09 GB)
     Array Size : 781417472 (745.22 GiB 800.17 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 0

    Update Time : Sun Jan  2 22:55:02 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : fd157a44 - correct
         Events : 3781914

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed

Drive 2 notice that raid device 0 is seen as removed.

~# mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : ddf5dbf5:499deb25:19ffd938:6715fbff (local to host localname)
  Creation Time : Fri Jun  1 23:34:11 2007
     Raid Level : raid5
  Used Dev Size : 390708736 (372.61 GiB 400.09 GB)
     Array Size : 781417472 (745.22 GiB 800.17 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 0

    Update Time : Sun Jan  2 22:57:10 2011
          State : clean
 Active Devices : 1
Working Devices : 1
 Failed Devices : 1
  Spare Devices : 0
       Checksum : fd157ae3 - correct
         Events : 3781917

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       0        0        0      removed
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed



```

I need to resume without losing the data, i'm afraid that adding drive 0 to array will reinitialize the array losing all of the data. Someone please help me out in finding the right command to get the array up long enough for me to get the important data off.(and please refrain from telling me how stupid i am for not getting it all off as soon as drive 2 went faulty. I know it was dumb but this is where i am now and can't change the past).
 Thanks,
 -D

---

