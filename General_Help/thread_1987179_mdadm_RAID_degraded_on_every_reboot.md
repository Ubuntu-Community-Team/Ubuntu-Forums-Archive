---
title: "mdadm RAID degraded on every reboot"
date: 2012-05-26
forum: General Help
---

### Post by acmeinc on 2012-05-26
This seems to be a pretty common problem, but I can't seem to find any answers.  I have a level 5 mdadm RAID setup.  On every reboot, a random device is degraded.  Attempts to add the device back to the array outputs:

```
mdadm /dev/md0 --add /dev/sdc1
mdadm: /dev/sdc1 reports being an active member for /dev/md0, but a --re-add fails.
mdadm: not performing --add as that would convert /dev/sdc1 in to a spare.
mdadm: To make this a spare, use "mdadm --zero-superblock /dev/sdc1" first.

```

This is fine and dandy, but it takes 16 hours to rebuild the array.  Not cool.  I need an alternate solution!  

I examine the "failed" device, which is just fine, checks out fine in SMART, and never actually throws errors.  The examine output is below:

```
mdadm --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : f0b2d5ee:a6bcb815:541b238a:cd75dc28
           Name : beta:0  (local to host beta)
  Creation Time : Wed May  2 01:45:20 2012
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3907025072 (1863.01 GiB 2000.40 GB)
     Array Size : 7814041600 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 3907020800 (1863.01 GiB 2000.39 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 0b1a3daf:2150f4bc:71173460:ca4c1eca

    Update Time : Sat May 26 01:01:39 2012
       Checksum : c91a6929 - correct
         Events : 39490

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AAA ('A' == active, '.' == missing)

```

That looks complete fine, right?!  So, the question is WHY is this device consider bad, but examine reports it just fine?  Also, is there some fancy command I can use to just FIX the superblock rather than waste a whole day rebuilding the array before I feel I can safely reboot my computer?

To make this even more peculiar, verbosity gives this during assembly:

```
mdadm: /dev/sde1 is identified as a member of /dev/md/0, slot 2.
mdadm: /dev/sdd1 is identified as a member of /dev/md/0, slot 1.
mdadm: /dev/sdc1 is identified as a member of /dev/md/0, slot 0.
mdadm: added /dev/sdc1 to /dev/md/0 as 0
mdadm: added /dev/sde1 to /dev/md/0 as 2
mdadm: added /dev/sdd1 to /dev/md/0 as 1
mdadm: /dev/md/0 has been started with 2 drives (out of 3).

```

Looks fine again, right?!  Totally weird.

For good measure, here's my --detail output:

```
/dev/md0:
        Version : 1.2
  Creation Time : Wed May  2 01:45:20 2012
     Raid Level : raid5
     Array Size : 3907020800 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 1953510400 (1863.01 GiB 2000.39 GB)
   Raid Devices : 3
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Sat May 26 01:34:36 2012
          State : clean, degraded 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : beta:0  (local to host beta)
           UUID : f0b2d5ee:a6bcb815:541b238a:cd75dc28
         Events : 39536

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       5       8       49        1      active sync   /dev/sdd1
       3       8       65        2      active sync   /dev/sde1

```

I should add this only started after upgraded to 12.04.  After upgrading, my mdadm was 0.90 meta, and it kept degrading.  So, I took a day to convert to 1.20...problem still persists.

Thanks.

---

