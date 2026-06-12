---
title: "Growing raid crashed now can't get assembled"
date: 2010-08-03
forum: General Help
---

### Post by phireant on 2010-08-03
First I want to apologize if this has been already posted but honestly I looked all over this forum and google for a full day now with nothing.

I was growing a 3 disk raid 5 to a 4 disk raid 6.  I used mdadm --grow /dev/md0 --level=6 --raid-devices=4 --backup-file=/home/user/Desktop/md0.backup for the grow.  The drive I added was /dev/sde1. Well it was going strong for like 2-3 days and last time I checked it was at 73% rebuild.  Well the frikin power went out on me and when I came back home I can't get the array assembled.

mdadm -V
mdadm - v3.1.2 - 10th March 2010


Here is my watch cat /proc/mdstat:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sdb1[0] sde1[3] sdc1[1] sdd1[2]
      7814057728 blocks super 0.91

unused devices: <none>


Here is my mdadm --detail /dev/md0:

/dev/md0:
        Version : 0.91
  Creation Time : Sat Apr 10 20:22:34 2010
     Raid Level : raid6
  Used Dev Size : 1953514432 (1863.02 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Aug  3 17:20:37 2010
          State : active, degraded, Not Started
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric-6
     Chunk Size : 64K

     New Layout : left-symmetric

           UUID : bb837e78:edd44bf4:4e5d5f89:3c47b7ba
         Events : 0.3177674

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      spare rebuilding   /dev/sde1


I have tried to mdadm --assemble --scan and get nothing.  I'm just at a loss and am more scared to do anything big before I had some different perspectives on this issue.  Then when I tried to force assemble:

sudo mdadm --assemble --force /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: /dev/sdb1 has no superblock - assembly aborted

I just have a fear that i lost my superblocks but I'm also a moron when it comes to this stuff.. I would like to think not, but I'm sure there are much smarter people than I on this issue.  Any help would help cause of course I have a lot of stuff on my raid with 3 2tb drives.. the irony is I was converting to raid 6 to make sure I had really good safety net.  

-Grant

---

### Post by jacekk015 on 2010-08-04
I think that you cannot do assemble because it's already assembled.
That's why it's complaining about sdb1 - that's a first drive. It's still active in the array.

Firstly - doing that kind of operation with adding devices and change level type without FULL backup... you know what. ;)

Give us:
```
sudo mdadm -E /dev/sdb
```It will show details from sdb drive.

[edit]
I've tried on my virtualbox RAID5
1) fail one drive
2) stop array
3) assemble scan - the array was automatically up and rebuilding
You cannot do assemble on assembled array.

You can do
```
sudo mdadm --stop /dev/md0
```And then
```
sudo mdadm --assemble --scan
```Look then on ```
sudo watch -n1 cat /proc/mdstat
```That should be safe but I cannot guarantee for 100%.

---

### Post by phireant on 2010-08-04
Thanks for the reply..  The worst part is I had to go to sleep last night and now I have to get to work. I have also done a grow with a raid 5 before just not raid 5 to raid 6 with a crash during the rebuild.. gosh i need to buy a battery backup badly.. but here is 

sudo mdadm -E /dev/sdb1:

/dev/sdb1:
          Magic : a92b4efc
        Version : 0.91.00
           UUID : bb837e78:edd44bf4:4e5d5f89:3c47b7ba
  Creation Time : Sat Apr 10 20:22:34 2010
     Raid Level : raid6
  Used Dev Size : 1953514432 (1863.02 GiB 2000.40 GB)
     Array Size : 3907028864 (3726.03 GiB 4000.80 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

  Reshape pos'n : 3029385216 (2889.05 GiB 3102.09 GB)
     New Layout : left-symmetric

    Update Time : Tue Aug  3 17:20:37 2010
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 5336aa22 - correct
         Events : 3177674

         Layout : left-symmetric-6
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active   /dev/sde1


Then when I stopped the array 'sudo mdadm --stop /dev/md0' and then tried to assemble with 'sudo mdadm --assemble --scan' it spit this out:

mdadm: Failed to restore critical section for reshape, sorry.
      Possibly you needed to specify the --backup-file


So when I was doing the grow I specified the backup file but I just don't have the time to mess with it because I need to get to work.. I want to thank you for your response though.. and after work I'll be trying it out and figuring out how to assemble with the backup file... thanks again

---

### Post by phireant on 2010-08-04
So home from work and and got it to start assembling.

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid6 sdb1[0] sdd1[2] sdc1[1]
      3907028864 blocks super 0.91 level 6, 64k chunk, algorithm 18 [4/3] [UUU_]
      [===============>.....]  reshape = 78.0% (1524168704/1953514432) finish=1270.4min speed=5632K/sec
```

AWESOME!!!!

I haven't tried to mount it, but all I did was stop the array and then issued an assemble but with the backup-file.

```
sudo mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 --backup-file=/home/phireant/Desktop/md0.backup
mdadm: restoring critical section
mdadm: /dev/md0 has been started with 3 drives (out of 4).
```

I am still a little confused that it started with 3 out of 4 drives.. or maybe that is because it still is technically the raid 5 still until it is done growing.. dunno.. Thanks for the help though I really appreciated it.

---

### Post by jacekk015 on 2010-08-05
That's why it's important to store, while grow, backup file NOT on RAID while growing.
mdadm informs about this before he starts to grow. You've made a good decision and now you're able to recover your array.

By the way.
You can increase minimal sync speed by changing file below [Kb/s]
/proc/sys/dev/raid/speed_limit_min

That is using more your hardware resources, but often server is not used while syncing or recover after failed drive. This parameter can be changed online, while syncing, and is working immediately.

---

