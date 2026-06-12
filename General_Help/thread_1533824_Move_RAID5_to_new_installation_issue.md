---
title: "Move RAID5 to new installation issue"
date: 2010-07-18
forum: General Help
---

### Post by RRacker on 2010-07-18
Hello,
I am using a software RAID5 consisting of three identical 640GB drives. It used to work well under Ubuntu 8.04LTS.
The array was clean, not degraded, no file system errors when I shut down my computer, removed the power from the three drives and installed Ubuntu 10.04LTS on a new additional disc.
After doing that I plugged in the power to the RAID drives again and, after a reboot, tried to add the RAID with 
sudo mdadm --assemble --scan
mdadm: /dev/md/0 has been started with 2 drives (out of 3) #-o
I tried

sudo mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: /dev/sda1 has no superblock - assembly aborted

Well, I plugged in my old Ubuntu 8.04 disc, booted and the RAID was there with all three discs.
Going back to the new installation I did :

sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Tue Jan 19 13:45:20 2010
     Raid Level : raid5
     Array Size : 1250258432 (1192.34 GiB 1280.26 GB)
  Used Dev Size : 625129216 (596.17 GiB 640.13 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent
    Update Time : Sun Jul 18 20:07:55 2010
          State : clean, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
   Layout : left-symmetric
   Chunk Size : 64K
           UUID : 7ad34912:3a9e8f0c:74dda04b:926c74f3 (local to host Ubu-Srv)
         Events : 0.415722
    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1

:icon_frown: for whatever reason the sda1 disc is removed from the array and I am unable to re-add it

sudo mdadm --manage --add /dev/md0 /dev/sda1
mdadm: Cannot open /dev/sda1: Device or resource busy
--
sudo mdadm -E /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 7ad34912:3a9e8f0c:74dda04b:926c74f3 (local to host srv)
  Creation Time : Tue Jan 19 13:45:20 2010
     Raid Level : raid5
  Used Dev Size : 625129216 (596.17 GiB 640.13 GB)
     Array Size : 1250258432 (1192.34 GiB 1280.26 GB)
   Raid Devices : 3
  Total Devices : 3
  Preferred Minor : 0
  Update Time : Sun Jul 18 19:07:54 2010
          State : clean
 Active Devices : 3
 Working Devices : 3
 Failed Devices : 0
 Spare Devices : 0
 Checksum : 22d0824d - correct
 Events : 415716
      Layout : left-symmetric
     Chunk Size : 64K
      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
:confused:
I can not mark the drive as failed, as it is already gone from the array,
I cannot add or re-add the drive to the array as it seems busy
--
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb1[1] sdc1[2]
      1250258432 blocks level 5, 64k chunk, algorithm 2 [3/2] [_UU]
   
md_d0 : inactive sda1[0](S)
      625129216 blocks
--
I noticed the sda1 as "inactive" and I found here
[http://man-wiki.net/index.php/8:mdadm](http://man-wiki.net/index.php/8:mdadm) 
**the switch --active**
             mark listed devices as active. (Only supported by multipath)
but obviously I either dont have multipath or the command is no longer supported

Hopefully somebody knows how to solve that (remember the array still works without problems under the old 8.04 installation)

thx
RRacker

---

### Post by RRacker on 2010-07-21
Finally I found it on my own. The solution is even visible in my first post if you know how to interpret the output of 
cat /proc/mdstat
md0 : active raid5 sdb1[1] sdc1[2]
      1250258432 blocks level 5, 64k chunk, algorithm 2 [3/2] [_UU] 

   For whatever reason the following "Raid" consisting of one disc without a type shows up
md_d0 : inactive sda1[0](S)
      625129216 blocks

I thought it was just a display or the info that there is another disc which seem to belong to some kind of an array but in fact it is a started array.
So when I executed : 
mdadm --stop /dev/md_d0 
it stopped, the disc sda1 was no longer busy and I could add it to the array md0 again which, in the meantime, I already created with the assume-clean switch and a "missing" disc.
I suspect I also could have stopped it again and do a --assemble --scan but well, now its rebuilding already:D

RRacker

---

### Post by rubylaser on 2010-07-21
After stopping md0, it might have been safer to zero out the superblock on that drive and then re-added it to the RAID array.  It shouldn't have created a seperate md device unless the superblocks where different.  Here's how you could have done that.
```
mdadm --zero-superblock /dev/sda1
```

It should workout okay for you, this would have just been a precaution.

---

