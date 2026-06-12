---
title: "lseek invalid argument error using pvdisplay command with raid 5"
date: 2006-04-27
forum: General Help
---

### Post by diff_sky on 2006-04-27
Hi,

I have setup software raid5 with 3 active devices, 1 spare.
Here's the output of mdadm --detail:
```

matthew@mammatus:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.01
  Creation Time : Thu Apr 27 00:56:00 2006
     Raid Level : raid5
     Array Size : 586099200 (558.95 GiB 600.17 GB)
    Device Size : 293049600 (279.47 GiB 300.08 GB)
   Raid Devices : 3
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Apr 27 21:42:45 2006
          State : clean, degraded, recovering
 Active Devices : 2
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 2

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 4% complete

           UUID : 2e763809:706de222:4bc3704d:083e37dc
         Events : 0.125

    Number   Major   Minor   RaidDevice State
       0      33        1        0      active sync   /dev/hde1
       1      34        1        1      active sync   /dev/hdg1
       2       0        0        -      removed

       3      57        1        -      spare   /dev/hdk1
       4      56        1        2      spare rebuilding   /dev/hdi1


```

You can see that I've degraded the array (I actually failed 2 devices, the reason I did follows) and it's happily rebuilding.

Before I did this failure test when I did: sudo pvdisplay, the spare disk in the array would always raise an error:
/dev/hdk1: lseek 4611824548366092288 failed: Invalid argument

I'm concerned because I don't know why this is (I'm pretty new to linux). Whilst the array is rebuilding, here's the output of sudo pvdisplay:

```

matthew@mammatus:~$ sudo pvdisplay
  /dev/hdi1: lseek 4611824548366092288 failed: Invalid argument
OUFDP0PXhi1Ix5Pa: using /dev/hdk1 not /dev/hdi1
  /dev/hdk1: lseek 4611824548366092288 failed: Invalid argument
  /dev/hdi1: lseek 4611824548366092288 failed: Invalid argument
OUFDP0PXhi1Ix5Pa: using /dev/hdk1 not /dev/hdi1
  /dev/hdk1: lseek 4611824548366092288 failed: Invalid argument
  /dev/hdi1: lseek 4611824548366092288 failed: Invalid argument
  /dev/hdi1: lseek 4611824548366092288 failed: Invalid argument
  /dev/hdi1: lseek 4611824548366092288 failed: Invalid argument
OUFDP0PXhi1Ix5Pa: using /dev/hdk1 not /dev/hdi1
  /dev/hdk1: lseek 4611824548366092288 failed: Invalid argument
  /dev/hdi1: lseek 4611824548366092288 failed: Invalid argument
OUFDP0PXhi1Ix5Pa: using /dev/hdk1 not /dev/hdi1
  /dev/hdk1: lseek 4611824548366092288 failed: Invalid argument
  --- NEW Physical volume ---
  PV Name               /dev/md0
  VG Name
  PV Size               558.94 GB
  Allocatable           NO
  PE Size (KByte)       0
  Total PE              0
  Free PE               0
  Allocated PE          0
  PV UUID               m6EQ9X-n775-1mwL-oMOU-FDP0-PXhi-1Ix5Pa

  --- NEW Physical volume ---
  PV Name               /dev/hdi1
  VG Name
  PV Size               248064.54 TB
  Allocatable           NO
  PE Size (KByte)       0
  Total PE              0
  Free PE               0
  Allocated PE          0
OU-FDP0-PXhi-1Ix5Pa     m\uffff\uffffR8\uffff-\uffff4\uffff-\uffffn\uffff1-o

  --- NEW Physical volume ---
  PV Name               /dev/hda3
  VG Name
  PV Size               71.97 GB
  Allocatable           NO
  PE Size (KByte)       0
  Total PE              0
  Free PE               0
  Allocated PE          0
  PV UUID               q4xfq8-7fjS-7KN3-EUg5-2yC3-cF8D-yDcdW7

```

Why am I getting the lseek errors? Is it because they are part of an array that is rebuilding? 
When the array is rebuilt why do I get the lseek error on the spare device?
And why is /dev/hdi being reported as having a size of 248064.54 TB?? :-k 

I'm eventually going to use this raid setup as a backup machine and I want to be certain that it is setup properly.

Thanks for any help :)

---

### Post by diff_sky on 2006-04-28
Any ideas anyone? :(

---

### Post by diff_sky on 2006-04-28
ok. Icreated a physical volume /dev/md0 ontop of the raid array and I'm getting the lseek error again. It seems a physical volume was also getting created upon /dev/hdi1.

I've simply done:
sudo pvcreate dev/md0
then
sudo pvremove hdi1

Now my sudo pvdisplay looks like this:
```

matthew@mammatus:~$ sudo pvdisplay
  --- NEW Physical volume ---
  PV Name               /dev/md0
  VG Name
  PV Size               558.95 GB
  Allocatable           NO
  PE Size (KByte)       0
  Total PE              0
  Free PE               0
  Allocated PE          0
  PV UUID               4nY2WW-xxYP-yyrL-WvfD-d9Hf-cetJ-xb0Mo4

  --- NEW Physical volume ---
  PV Name               /dev/hda3
  VG Name
  PV Size               71.97 GB
  Allocatable           NO
  PE Size (KByte)       0
  Total PE              0
  Free PE               0
  Allocated PE          0
  PV UUID               q4xfq8-7fjS-7KN3-EUg5-2yC3-cF8D-yDcdW7

```

Which looks ok now. :)

And for those interested, here are the array details:

```

matthew@mammatus:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.01
  Creation Time : Thu Apr 27 00:56:00 2006
     Raid Level : raid5
     Array Size : 586099200 (558.95 GiB 600.17 GB)
    Device Size : 293049600 (279.47 GiB 300.08 GB)
   Raid Devices : 3
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Apr 28 08:29:36 2006
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 2e763809:706de222:4bc3704d:083e37dc
         Events : 0.130

    Number   Major   Minor   RaidDevice State
       0      33        1        0      active sync   /dev/hde1
       1      34        1        1      active sync   /dev/hdg1
       2      56        1        2      active sync   /dev/hdi1

       3      57        1        -      spare   /dev/hdk1


```

---

