---
title: "How to auto start my array in mdadm"
date: 2011-04-10
forum: General Help
---

### Post by Kimbie on 2011-04-10
I have created a RAID 5 array using the built in Disk Utility.

This is great and formatted it with ext4, and mounted it.

However on reboot  in Disk Utility as RAID Array is not running and under state Not running, partially assembled.

I have to stop the array then restart it, then mount it before I can access what is on it.

Obviously this is not very good as I often have the system shutdown at night to converse energy, and having to do this every time it boots is a pain.

Could someone please explain in plain english what I need to go to get my array to start and mount on startup

Thanks

---

### Post by sam123 on 2011-04-10
1. Append the output of sudo mdadm --detail --scan to /etc/mdadm/mdadm.conf
2. Make entries in /etc/fstab

Refer to [http://ubuntuforums.org/showthread.php?t=1312539](http://ubuntuforums.org/showthread.php?t=1312539)

---

### Post by mn_voyageur on 2011-04-10
I appear to have everything entered, however, I do not auto start my RAID either.

Any help would be appreciated.

MarkN

---

### Post by sam123 on 2011-04-10
I'll post my configuration in case it helps you.

I have a RAID 1 array from /dev/sdb1 and /dev/sdc1 mounted on /home

My /etc/mdadm/mdadm.conf contains:
DEVICE partitions
DEVICE /dev/sdc1 /dev/sdb1

ARRAY /dev/md0 level=raid1 num-devices=2 metadata=0.90 UUID=8e53883c:e96bbfd1:a4052542:b9f12818

My fstab contains:
/dev/md0	/home	ext3	defaults 0 0 

In case you're having trouble, post your /etc/fstab, /etc/mdadm/mdadm.conf and the output of sudo mdadm --detail --scan

---

### Post by mn_voyageur on 2011-04-12
Okay, I seem to have another problem.  

The drives are there.  According to Disk Utility, they are mounted and healthy.  When I first rebooted, sba was "removed."  I rebooted and another disappeared.  This last time a third disappeared.

/dev/md0:
        Version : 00.90
  Creation Time : Mon Feb 21 05:24:20 2011
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 4
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Apr 12 05:53:55 2011
          State : active, degraded, Not Started
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : b40cc711:46ef5048:1178d5b1:7b4fd811 (local to host 10)
         Events : 0.198

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       0        0        1      removed
       2       0        0        2      removed
       3       8       17        3      active sync   /dev/sdb1


When I check the array:
Error checking array: helper exited with exit code 1: device /dev/md_d0 is not idle

All of the drives are healthy and considered part of the array.

---

