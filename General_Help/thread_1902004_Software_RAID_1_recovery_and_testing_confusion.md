---
title: "Software RAID 1 recovery and testing confusion"
date: 2011-12-29
forum: General Help
---

### Post by paulgj on 2011-12-29
Hello,

I have a Ubuntu Server 11.10 installed in software RAID 1 based on the instructions on the [_Advanced Installation_]("https://help.ubuntu.com/11.10/serverguide/C/advanced-installation.html") page.

Now I want to test breaking and recovering the array by disconnecting a drive, booting in degraded mode and then installing a new drive and re-syncing.  The instructions [_here_]("https://help.ubuntu.com/11.10/serverguide/C/advanced-installation.html#raid-maintenance") indicate that once in degraded mode I just need to **--remove** the disk from both md0 and md1 devices, reinstall a new disk and then **--add** the new device back to md0 and md1.  

It appears at this point that the disk will then begin re-syncing and progress can be watched via the [FONT="Courier New"]watch -n1 cat /proc/mdstat[/FONT] command.

Is that it? no need to set up partitions or anything before doing this step?

The part that confuses me if where it mentions to re install Grub onto the new disk with [FONT="Courier New"]sudo grub-install /dev/md0[/FONT].  Shouldn't this command be [FONT="Courier New"]sudo grub-install /dev/sdx[/FONT] where x is the id of the replaced drive?  Wouldn't the md devices already contain grub from the boot of the non-failed drive?  Guess I'm confused here.

Here is my current raid setup in case it helps:
```

paul@ubuntu:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 sda2[0] sdb2[1]
      70335416 blocks super 1.2 [2/2] [UU]

md0 : active raid1 sda1[0] sdb1[1]
      7810036 blocks super 1.2 [2/2] [UU]

unused devices: <none>

paul@ubuntu:~$ sudo mdadm -D /dev/md0
[sudo] password for paul:
/dev/md0:
        Version : 1.2
  Creation Time : Tue Dec 27 22:12:18 2011
     Raid Level : raid1
     Array Size : 7810036 (7.45 GiB 8.00 GB)
  Used Dev Size : 7810036 (7.45 GiB 8.00 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Thu Dec 29 14:55:16 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : ubuntu:0  (local to host ubuntu)
           UUID : 87eb9c6b:e38970ce:47d97e62:3eec87f1
         Events : 19

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1

paul@ubuntu:~$ sudo mdadm -D /dev/md1
/dev/md1:
        Version : 1.2
  Creation Time : Tue Dec 27 22:12:26 2011
     Raid Level : raid1
     Array Size : 70335416 (67.08 GiB 72.02 GB)
  Used Dev Size : 70335416 (67.08 GiB 72.02 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Thu Dec 29 15:56:49 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : ubuntu:1  (local to host ubuntu)
           UUID : d122e399:ee10f81d:132e1c8d:c1a3d942
         Events : 32

    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       1       8       18        1      active sync   /dev/sdb2


```

Thanks in advance for any help on this subject :eek:

---

