---
title: "Please help for RAID 5 failure"
date: 2011-08-06
forum: General Help
---

### Post by yota73 on 2011-08-06
Hi, I'm in this situation:
Ubuntu 11.04
4x2Tb SATA drives in RAID 5
Last week 1 of this drives crash and I remove it from the array fisically. 
Then I reboot the system and all works ok in degraded mode.

Now I put a new drive in the array and this is the result:

md0 : inactive sdd1[1](S) sde1[4](S) sdb1[5](S) sdc1[2](S)
      7814043908 blocks super 1.2
       
unused devices: <none>
root@MediaServer:/home/vittorio/Scaricati/raidextract-0.2.2# mdadm --detail /dev/md0
mdadm: md device /dev/md0 does not appear to be active.
root@MediaServer:/home/vittorio/Scaricati/raidextract-0.2.2# mdadm --manage --force --run /dev/md0
mdadm: failed to run array /dev/md0: Input/output error
root@MediaServer:/home/vittorio/Scaricati/raidextract-0.2.2# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Tue Jul  5 15:24:27 2011
     Raid Level : raid5
  Used Dev Size : 1953510400 (1863.01 GiB 2000.39 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent

    Update Time : Sat Aug  6 16:17:44 2011
          State : active, FAILED, Not Started
 Active Devices : 2
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 2

         Layout : left-symmetric
     Chunk Size : 512K

           Name : :MediaServer RAID 5
           UUID : b448f2e2:48872dd7:3135fa97:fde77780
         Events : 14234

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       49        1      active sync   /dev/sdd1
       2       8       33        2      active sync   /dev/sdc1
       3       0        0        3      removed

       4       8       65        -      spare   /dev/sde1
       5       8       17        -      spare   /dev/sdb1


The /dev/sde1 is the spare disk that works until yesterday and the /dev/sdb1 is the new drive that sobstitute the brojen one.

Can I fix the problem I try 1000 solutions but nothing works.

Please help a desperate new linux user.

Thanks

---

### Post by yota73 on 2011-08-07
Any help please ](*,)

---

