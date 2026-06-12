---
title: "Need help repairing my crashed RAID5"
date: 2012-03-28
forum: General Help
---

### Post by KenRocks on 2012-03-28
Left my machine downloading last night and came in to find it booted to the GRUB screen in the morning. When I selected regular linux, it gave me a warning that my RAID was degenerate and asked if I wanted to start it anyway...I said sure, it flashed a few errors too quickly for me to read, then went to the recovery console.

When I run mdadm --detail I get:


skynet@Skynet:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Thu Apr 14 12:18:33 2011
     Raid Level : raid5
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Mar 28 18:58:04 2012
          State : active, degraded, Not Started
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 6d29fb0a:244efab7:e3119a90:8bf005c0 (local to host Skynet)
         Events : 0.33703

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       48        1      active sync   /dev/sdd
       2       0        0        2      removed
       3       8       64        3      active sync   /dev/sde

       4       8       32        -      spare   /dev/sdc

This is after I messed around with one of the drives, found that it wasnt simply unplugged/bad power cord/etc. I bought an identical spare and used mdadm --add to add it to my RAID. Now it shows as a spare.

It doesnt repair automatically, and I still can't start the RAID.

I tried mdadm --assemble and listed off the components to the RAID...


skynet@Skynet:~$ sudo mdadm --assemble /dev/md0 /dev/sdb /dev/sdc /dev/sdd /dev/sde
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: /dev/sdb has no superblock - assembly aborted

I can't seem to do it in the disk manager GUI either...

I'm not sure what I'm missing. It lists as a spare...how do I get it to replace the busted one?

(OS is Lubuntu 11.10)

---

### Post by KenRocks on 2012-03-28
And heres my mdstat file...


skynet@Skynet:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdc[4](S) sdb[0] sde[3] sdd[1]
      7814057984 blocks
       
unused devices: <none>

---

### Post by KenRocks on 2012-03-28
I found a blog post suggesting the fix was to simply mdadm --create the RAID again, and that mdadm would recognize the member drives used to be part of the same RAID and attempt to reconstruct them.

[http://kevin.deldycke.com/2007/03/how-to-recover-a-raid-array-after-having-zero-ized-superblocks/](http://kevin.deldycke.com/2007/03/how-to-recover-a-raid-array-after-having-zero-ized-superblocks/)

I'm tempted to try it, but I've noticed a difference in my setup compared to everyone elses:  when I first created the RAID, I used /dev/sdb instead of /dev/sdb1 for each of the component drives. 

I'm kind of terrified to try it, so far, since there's some 5 years of data on there that I don't want to lose...is this on the right track?

---

