---
title: "mdadm RAID5 issue &quot;appear to have very similar superblocks&quot;"
date: 2011-02-17
forum: General Help
---

### Post by Snowjoggs on 2011-02-17
One of the disks in my RAID5 arrays started acting up, giving me some I/O buffer errors and making the RAID stop.

disk info

```
=== START OF INFORMATION SECTION ===
Device Model:     WDC WD10EARS-00Y5B1
Serial Number:    WD-WMAV51466805
Firmware Version: 80.00A80
User Capacity:    1,000,204,886,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Feb 17 16:26:53 2011 CET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

```

So I burned the WD diag tool "Data lifeguard diagnostic" to a boot CD and ran the extensive test on the bad drive only. It reported error 223 and that it had fixed the problem

I re-assembled my system, now the following happens if I try to start the array

```
root@enterprise:~# mdadm --assemble --scan /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
mdadm: WARNING /dev/sdb1 and /dev/sdc1 appear to have very similar superblocks.
      If they are really different, please --zero the superblock on one
      If they are the same or overlap, please remove one from the
      DEVICE list in mdadm.conf.

```

Did the WD diag tool write something to the drive to corrupt it perhaps?

What should I do from here? kind of green when it comes to MDADM :(

Some more infos

```
root@enterprise:~# mdadm --examine /dev/sdc1
mdadm: metadata format 00.90 unknown, ignored.
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 1ea42a9a:8a44e4c2:163c2a05:89fa2e07
  Creation Time : Tue Jun  1 22:34:37 2010
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 4883799680 (4657.55 GiB 5001.01 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0

    Update Time : Sun Feb 13 16:33:03 2011
          State : active
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0
       Checksum : c5f0cfb0 - correct
         Events : 1016773

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       0        0        0      spare

   0     0       0        0        0      spare
   1     0       0        0        0      spare
   2     0       0        0        0      spare
   3     0       0        0        0      spare
   4     0       0        0        0      spare
   5     0       0        0        0      spare

```

---

### Post by psusi on 2011-02-17
Yes, it looks like it corrupted the md superblock.  I'd say run mdadm --zero-superblocks /dev/sdc1 to wipe it clean, then you should be able to activate the array in degraded mode, then add sdc1 back into the array and let it rebuild.

---

### Post by Snowjoggs on 2011-02-17
> **psusi said:**
> Yes, it looks like it corrupted the md superblock.  I'd say run mdadm --zero-superblocks /dev/sdc1 to wipe it clean, then you should be able to activate the array in degraded mode, then add sdc1 back into the array and let it rebuild.

Thanks for the quick reply!

Just so I do not mess anything up, can you verify that this would be

```
 mdadm --zero-superblock /dev/sdc1
mdadm --assemble --scan /dev/md0
mdadm --add /dev/sdc1

```

?

---

### Post by psusi on 2011-02-17
You need to specify which array to add to:

mdadm /dev/md0 --add /dev/sdc1

---

### Post by Snowjoggs on 2011-02-17
```
root@enterprise:~# mdadm --zero-superblock /dev/sdc1
mdadm: metadata format 00.90 unknown, ignored.

```

```

root@enterprise:~# mdadm --assemble --scan /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
mdadm: /dev/md0 assembled from 4 drives - not enough to start the array.
root@enterprise:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sdd1[2](S) sdg1[5](S) sdf1[4](S) sde1[3](S) sdb1[0](S)
      4883799680 blocks

unused devices: <none>

```

```

root@enterprise:~# mdadm --detail /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
mdadm: md device /dev/md0 does not appear to be active.

```

```
root@enterprise:~# mdadm --examine /dev/sdb1
mdadm: metadata format 00.90 unknown, ignored.
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 1ea42a9a:8a44e4c2:163c2a05:89fa2e07
  Creation Time : Tue Jun  1 22:34:37 2010
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 4883799680 (4657.55 GiB 5001.01 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0

    Update Time : Sun Feb 13 16:33:03 2011
          State : active
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0
       Checksum : c5f0d197 - correct
         Events : 1016773

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync   /dev/sdg1

```

hmm.. now what?

---

### Post by Snowjoggs on 2011-02-17
Also..

```
root@enterprise:~# mdadm --add /dev/md0 /dev/sdc1
mdadm: metadata format 00.90 unknown, ignored.
mdadm: cannot get array info for /dev/md0
```

---

### Post by YesWeCan on 2011-02-17
It may help to also show the output of:

cat /proc/mdstat

sudo blkid

---

### Post by Snowjoggs on 2011-02-17
> **YesWeCan said:**
> It may help to also show the output of:

cat /proc/mdstat

sudo blkid


Here it is

```

root@enterprise:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sdd1[2](S) sdg1[5](S) sdf1[4](S) sde1[3](S) sdb1[0](S)
      4883799680 blocks

unused devices: <none>
root@enterprise:~# blkid
/dev/sda1: UUID="0fa38212-aab2-43cb-9623-51d7d4f62c1d" TYPE="ext2"
/dev/sda5: UUID="Ki6J6Y-gKz1-SdFh-V0ki-vU5I-wYZ8-IbxdSX" TYPE="LVM2_member"
/dev/sdb1: UUID="1ea42a9a-8a44-e4c2-163c-2a0589fa2e07" TYPE="linux_raid_member"
/dev/sdd1: UUID="1ea42a9a-8a44-e4c2-163c-2a0589fa2e07" TYPE="linux_raid_member"
/dev/sde1: UUID="1ea42a9a-8a44-e4c2-163c-2a0589fa2e07" TYPE="linux_raid_member"
/dev/mapper/enterprise-root: UUID="46cad95a-44f9-467c-a42a-f8e7a66b65a6" TYPE="ext4"
/dev/mapper/enterprise-swap_1: UUID="b05fddc0-439d-4c96-9065-d9ed4bea92ef" TYPE="swap"
/dev/sdf1: UUID="1ea42a9a-8a44-e4c2-163c-2a0589fa2e07" TYPE="linux_raid_member"
/dev/sdg1: UUID="1ea42a9a-8a44-e4c2-163c-2a0589fa2e07" TYPE="linux_raid_member"
root@enterprise:~#
```

---

### Post by YesWeCan on 2011-02-17
Have you disconnected sdc? It does not appear in the blkid output.

---

### Post by Snowjoggs on 2011-02-17
> **YesWeCan said:**
> Have you disconnected sdc? It does not appear in the blkid output.

No.. its still connected...

```
root@enterprise:~# smartctl -i /dev/sdc
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD10EARS-00Y5B1
Serial Number:    WD-WMAV51466805
Firmware Version: 80.00A80
User Capacity:    1,000,204,886,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Feb 17 18:57:14 2011 CET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

```

---

### Post by YesWeCan on 2011-02-17
Let's see
sudo fdisk -l /dev/sdc

---

### Post by Snowjoggs on 2011-02-17
> **YesWeCan said:**
> Let's see
sudo fdisk -l /dev/sdc

root@enterprise:~# fdisk -l /dev/sdc

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   fd  Linux raid autodetect

---

### Post by YesWeCan on 2011-02-17
I am not an expert and it isn't obvious to me what is wrong. It seems odd that mdadm refuses to assemble the array on account of only having 4 devices available when it subsequently lists 5! So let me take a wild guess and suggest that the presence of sdc is confusing mdadm for some reason. So if you were to physically disconnect sdc and then try to assemble md0 it might be happier. I would try this.
I think it odd that sdc does not show in the blkid list.
Also, have a look yourself at the fdisk -l output for all the array disks and check they look the same.

---

### Post by Snowjoggs on 2011-02-17
> **YesWeCan said:**
> I am not an expert and it isn't obvious to me what is wrong. It seems odd that mdadm refuses to assemble the array on account of only having 4 devices available when it subsequently lists 5! So let me take a wild guess and suggest that the presence of sdc is confusing mdadm for some reason. So if you were to physically disconnect sdc and then try to assemble md0 it might be happier. I would try this.
I think it odd that sdc does not show in the blkid list.
Also, have a look yourself at the fdisk -l output for all the array disks and check they look the same.


Ugh 

```
mdadm: metadata format 00.90 unknown, ignored.
mdadm: /dev/md0 assembled from 3 drives - not enough to start the array.
```

Only 3 this time?!

```
/dev/sda1: UUID="0fa38212-aab2-43cb-9623-51d7d4f62c1d" TYPE="ext2"
/dev/sda5: UUID="Ki6J6Y-gKz1-SdFh-V0ki-vU5I-wYZ8-IbxdSX" TYPE="LVM2_member"
/dev/sdb1: UUID="1ea42a9a-8a44-e4c2-163c-2a0589fa2e07" TYPE="linux_raid_member"
/dev/sdd1: UUID="1ea42a9a-8a44-e4c2-163c-2a0589fa2e07" TYPE="linux_raid_member"
/dev/mapper/enterprise-root: UUID="46cad95a-44f9-467c-a42a-f8e7a66b65a6" TYPE="ext4"
/dev/mapper/enterprise-swap_1: UUID="b05fddc0-439d-4c96-9065-d9ed4bea92ef" TYPE="swap"
/dev/sde1: UUID="1ea42a9a-8a44-e4c2-163c-2a0589fa2e07" TYPE="linux_raid_member"
/dev/sdf1: UUID="1ea42a9a-8a44-e4c2-163c-2a0589fa2e07" TYPE="linux_raid_member"

```

```
root@enterprise:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sdd1[3](S) sdf1[5](S) sde1[4](S) sdb1[0](S)
      3907039744 blocks

unused devices: <none>

```

---

### Post by psusi on 2011-02-17
sdc is missing because the superblock has been zeroed.  The question is, why are the other drives missing?  What do you get from:

mdadm -E /dev/sd[bcdefg]1

---

### Post by Snowjoggs on 2011-02-17
> **psusi said:**
> sdc is missing because the superblock has been zeroed.  The question is, why are the other drives missing?  What do you get from:

mdadm -E /dev/sd[bcdefg]1

```
root@enterprise:~# mdadm -E /dev/sd[bcdefg]1
mdadm: metadata format 00.90 unknown, ignored.
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 1ea42a9a:8a44e4c2:163c2a05:89fa2e07
  Creation Time : Tue Jun  1 22:34:37 2010
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 4883799680 (4657.55 GiB 5001.01 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0

    Update Time : Sun Feb 13 16:33:03 2011
          State : active
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0
       Checksum : c5f0d197 - correct
         Events : 1016773

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync
mdadm: No md superblock detected on /dev/sdc1.
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 1ea42a9a:8a44e4c2:163c2a05:89fa2e07
  Creation Time : Tue Jun  1 22:34:37 2010
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 4883799680 (4657.55 GiB 5001.01 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0

    Update Time : Sun Feb 13 16:34:44 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 0
       Checksum : c600561c - correct
         Events : 1016776

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       65        3      active sync   /dev/sde1

   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync
/dev/sde1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 1ea42a9a:8a44e4c2:163c2a05:89fa2e07
  Creation Time : Tue Jun  1 22:34:37 2010
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 4883799680 (4657.55 GiB 5001.01 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0

    Update Time : Sun Feb 13 16:34:44 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 0
       Checksum : c600562e - correct
         Events : 1016776

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8       81        4      active sync   /dev/sdf1

   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync
/dev/sdf1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 1ea42a9a:8a44e4c2:163c2a05:89fa2e07
  Creation Time : Tue Jun  1 22:34:37 2010
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 4883799680 (4657.55 GiB 5001.01 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0

    Update Time : Sun Feb 13 16:34:44 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 0
       Checksum : c6005640 - correct
         Events : 1016776

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     5       8       97        5      active sync

   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync


```

---

### Post by YesWeCan on 2011-02-17
Curious.
So sdb appears to have been removed from the array and sdg doesn't have its path listed.
Perhaps sdb was removed at the time that sdb1 and sdc1 were declared to have "too similar" super-blocks (whatever that means). So perhaps adding /dev/sdb1 is required.

psusi will know.

---

### Post by Snowjoggs on 2011-02-17
Pretty confused myself :S

FYI my RAID5 array consist of 6x1TB disk

root@enterprise:~# cat /etc/mdadm/mdadm.conf
DEVICE /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1
ARRAY /dev/md0 level=raid5 num-devices=6 metadata=00.90 UUID=1ea42a9a:8a44e4c2:163c2a05:89fa2e07

---

### Post by YesWeCan on 2011-02-17
My guess is that you will need to disconnect sdc and re-add sdb1. When you originally reconnected sdc mdadm complained about a super-block clash between sdc1 and sdb1. Presumably, this caused mdadm to "remove" sdb1 but not to "fail" it. So perhaps after disconnecting sdc you can try
'sudo mdadm /dev/md0 --re-add /dev/sdb1'
and then try assembling it.

If that works we'll have to figure out how to make sdc usable again.

---

### Post by Snowjoggs on 2011-02-17
> **YesWeCan said:**
> My guess is that you will need to disconnect sdc and re-add sdb1. When you originally reconnected sdc mdadm complained about a super-block clash between sdc1 and sdb1. Presumably, this caused mdadm to "remove" sdb1 but not to "fail" it. So perhaps after disconnecting sdc you can try
'sudo mdadm /dev/md0 --re-add /dev/sdb1'
and then try assembling it.

If that works we'll have to figure out how to make sdc usable again.

```
root@enterprise:~# mdadm /dev/md0 --re-add /dev/sdb1
mdadm: metadata format 00.90 unknown, ignored.
mdadm: cannot get array info for /dev/md0

```

What is also weird is that if sdc is disconnected sdg will not show up (I see it showing in the BIOS tho). If I connect sdc, then sdg also shows....

---

### Post by Snowjoggs on 2011-02-17
Got it working :D

1.
```
root@enterprise:~# mdadm --stop /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
mdadm: stopped /dev/md0

```2.
```
root@enterprise:~# mdadm --assemble --scan --force /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
mdadm: /dev/md0 has been started with 5 drives (out of 6).

```3.
```
root@enterprise:~# mdadm /dev/md0 --re-add /dev/sdc1
mdadm: metadata format 00.90 unknown, ignored.
mdadm: added /dev/sdc1

```Voilà

```
root@enterprise:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdc1[6] sdb1[0] sdg1[5] sdf1[4] sde1[3] sdd1[2]
      4883799680 blocks level 5, 64k chunk, algorithm 2 [6/5] [U_UUUU]
      [>....................]  recovery =  0.0% (70528/976759936) finish=692.2min speed=23509K/sec

unused devices: <none>

```


mdadm is not for the faint hearted, got 5TB worth of stuff there :S

---

### Post by Snowjoggs on 2011-02-17
One final question... I would like to re-assemble the box and let it re-sync in a bit less noisy-for-me environment. Is it safe to do a normal shutdown while its re-syncing, will it not simply start to sync again from where it left off?

---

### Post by YesWeCan on 2011-02-17
Good :D
Phew, eh?

Ok, so I have learned something. When in doubt , force it!
Geez.

It would help if I could find some proper mdadm documentation (not just the man page).

Advice to the wise: back it up asap. When one drive fails the odds may be higher of another failing.
RAID5 is not the most reliable RAID. RAID6 is a little better and RAID10 is much better.

---

### Post by YesWeCan on 2011-02-17
> **Snowjoggs said:**
> One final question... I would like to re-assemble the box and let it re-sync in a bit less noisy-for-me environment. Is it safe to do a normal shutdown while its re-syncing, will it not simply start to sync again from where it left off?
See what it says in the manual! :p
I imagine it will just carry on. As it is resyncing sdc from scratch, anyhow, it probably won't matter. But that's just an educated guess.

---

### Post by Snowjoggs on 2011-02-17
Can you explain how RAID10 works. E.g. can my RAID5 be converted to RAID10 and how much "less" data would be available for storage on my 6TB array?

---

### Post by YesWeCan on 2011-02-17
> **Snowjoggs said:**
> Can you explain how RAID10 works. E.g. can my RAID5 be converted to RAID10 and how much "less" data would be available for storage on my 6TB array?
RAID10 is also called RAID 1+0. It means you have a set of 2-disk mirrors that are striped to. It is very fast but only 50% capacity efficient. It does not use distributed parity...so if a disk fails the rebuild relies only on its twin rather than relying on all the remaining disks being readable.

With 6 x 1TB disks
RAID10 = 3TB
RAID6 = 4TB
RAID5 = 5TB

RAID6 is significantly better than RAID5. It is basically the same thing but with double the parity bits so it can, in theory, recovery from the loss of 2 disks. Another downside of RAID5 and moreso of RAID6 is that they are slowed down on writing by having to generate all the parity bits.

There are subtle failure modes that anyone using a RAID5 or 6 should be aware of if they are concerned about their data. For example, see: [http://www.informix.com.ua/filtered/msg00073.shtml](http://www.informix.com.ua/filtered/msg00073.shtml)

---

### Post by Snowjoggs on 2011-02-17
Thank you for the thorough response. I will google the method for converting to RAID6 or RAID10 and will create a new thread if I run into any trouble.

Also thank you both for your assistance with my issue :)

---

### Post by YesWeCan on 2011-02-17
I think you really figured it out by yourself but you are welcome none the less.

I am not aware of a simple means to convert one array type to another, other than a full backup/restore. But I am not an expert in this area (yet).

Just for completeness, another member **rubylaser** told me the other day that RAID5 arrays, and presumably RAID6 too, ought to be run on UPS to avoid a potential problem called the "write hole". This concerns a corruption issue when a write operation is being interrupted between writing data and writing the parity for that data. This can potentially occur during a power outage. The odds of this may be very small for all I know but a UPS was mentioned as a sensible precaution.

---

### Post by psusi on 2011-02-17
> **Snowjoggs said:**
> One final question... I would like to re-assemble the box and let it re-sync in a bit less noisy-for-me environment. Is it safe to do a normal shutdown while its re-syncing, will it not simply start to sync again from where it left off?

Yes, it is safe ( assuming you don't have another disk fail on you when you start up ).  Whether it resumes where it left off, or has to start over depends on whether or not you have enabled a write intent bitmap.

> **YesWeCan said:**
> 
RAID5 is not the most reliable RAID. RAID6 is a little better and RAID10 is much better.

Actually raid6 is better than raid10, since it can withstand 2 failures.  Raid10 can only withstand 2 under certain circumstances, otherwise it is only 1.  It also wastes more space.

> **YesWeCan said:**
> RAID10 is also called RAID 1+0. It means you have a set of 2-disk mirrors that are striped to. It is very fast but only 50% capacity efficient. It does not use distributed parity...so if a disk fails the rebuild relies only on its twin rather than relying on all the remaining disks being readable.

Some vendors use the term "raid10" when they really mean raid 1+0.  They are not the same thing, at least as far as mdadm is concerned.  raid 1+0 requires an even number of disks >= 4.  raid10 can use any number ( even or odd ) of disks >= 2.  With real raid10, each data block is duplicated on another disk ( usually the next one in the stripe ), but with 1+0 which block is duplicated where is based solely on which disk it is on.

Raid10 can also be configured to store the duplicate far from the original ( like on the bottom half of the disk ), or on the next stripe but offset, instead of the next disk in the stripe.  Far mode gives read throughput equal to raid0, but the write throughput suffers.  Offset mode is more of a balance.

---

### Post by YesWeCan on 2011-02-17
> **psusi said:**
> Actually raid6 is better than raid10, since it can withstand 2 failures.  Raid10 can only withstand 2 under certain circumstances, otherwise it is only 1.  It also wastes more space.
Well this is an area I am interested in. I do not agree. That is, I do not agree that having a capability to recover 2 disks necessarily results in a safer array. This is counter-intuitive. This is because of the distributed parity putting a dependency on all the disks in the array. I have run some statistical models on this and I find that, based just on the published read fail rate of ordinary disks, that RAID6 is actually less reliable than RAID10 if one uses more than 4 or so disks. This does not include the subtle failure modes that distributed parity introduces nor the increased probability of drive failure after the first drive has failed. Also, RAID10 can can recover between 1 and half your disks, depending on which disks fail. Then there is the matter of the ease of recovering data if the array fails.

> Some vendors use the term "raid10" when they really mean raid 1+0.  They are not the same thing, at least as far as mdadm is concerned.  raid 1+0 requires an even number of disks >= 4.  raid10 can use any number ( even or odd ) of disks >= 2.  With real raid10, each data block is duplicated on another disk ( usually the next one in the stripe ), but with 1+0 which block is duplicated where is based solely on which disk it is on.

Raid10 can also be configured to store the duplicate far from the original ( like on the bottom half of the disk ), or on the next stripe but offset, instead of the next disk in the stripe.  Far mode gives read throughput equal to raid0, but the write throughput suffers.  Offset mode is more of a balance.
Thanks. I was referring to an even number of disks, so RAID 1+0. I thought RAID 10 was generally considered synonymous with RAID 1+0.

---

### Post by YesWeCan on 2011-02-17
@psusi
Here is my array. Would you help me understand what these mean?
Layout : near=2, far=1
Events : 0.153964

Thx.

```
$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Thu Jan 13 18:21:56 2011
     Raid Level : raid10
     Array Size : 1953314688 (1862.83 GiB 2000.19 GB)
  Used Dev Size : 976657344 (931.41 GiB 1000.10 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Feb 17 21:39:58 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : near=2, far=1
     Chunk Size : 64K

           UUID : f3c98c9c:74235cf2:6ded50c4:977e48b4
         Events : 0.153964

    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       1       8       18        1      active sync   /dev/sdb2
       2       8       34        2      active sync   /dev/sdc2
       3       8       50        3      active sync   /dev/sdd2

```

---

### Post by YesWeCan on 2011-02-17
I managed to figure out the near and far notation on my own. See: [http://en.wikipedia.org/wiki/Non-standard_RAID_levels](http://en.wikipedia.org/wiki/Non-standard_RAID_levels)

*For others who may be interested:*
Disk sectors may be duplicated across disks and can also be duplicated along disks. The "near" number is how many across duplicates there are and "far" is how many along duplicates.

The total duplicates = near x far.

The far duplication is achieved by splitting the "length" of each disk (as if each disk were a single line of sectors) into equal parts. For far=2 each disk is divided into two along its length. In addition, sectors duplicated along the length are also offset by one disk (for speed reasons, I believe).

So a RAID 1 and a RAID 1+0 have near=2 (two copies of each sector across) and far=1 (no lengthwise splitting: the disks are divided in length by 1).

The format of striping of "chunks" across RAID 1 disk pairs is something else again. More to find out about. :)

---

### Post by psusi on 2011-02-17
> **YesWeCan said:**
> Well this is an area I am interested in. I do not agree. That is, I do not agree that having a capability to recover 2 disks necessarily results in a safer array. This is counter-intuitive. This is because of the distributed parity putting a dependency on all the disks in the array. I have run some statistical models on this and I find that, based just on the published read fail rate of ordinary disks, that RAID6 is actually less reliable than RAID10 if one uses more than 4 or so disks.

You are doing something wrong then.  The probability of 2 failures is less likely than 1 failure no matter how you slice it.

> **YesWeCan said:**
> This does not include the subtle failure modes that distributed parity introduces nor the increased probability of drive failure after the first drive has failed.

What failure modes?  And the probability of additional failures is the same no matter if you use raid10 or raid6.

> **YesWeCan said:**
> Also, RAID10 can can recover between 1 and half your disks, depending on which disks fail. Then there is the matter of the ease of recovering data if the array fails.

That is true of raid 1+0, but not raid10.  For a 6 disk array, raid6 has a 100% success rate with 1 failure, 100% with 2 failures, and 0% with 3 or more.  raid 1+0 has a 100% success rate with 1 failure, 66% with 2 failures, 33% with 3 failures, 0% with 4+.  The probability of 3 simultaneous failures is much less than 2, so the +33% raid1+0 has in the 3 disk failure case over raid6 does not come close to making up for the -33% success it has in the face of 2 failures.

> **YesWeCan said:**
> 
The total duplicates = near x far.


near + far + offset, not near x far.

---

### Post by YesWeCan on 2011-02-18
> **psusi said:**
> You are doing something wrong then.  The probability of 2 failures is less likely than 1 failure no matter how you slice it.
It is possible I have made a mistake. What you say is obviously true. However, the way I look at it, the question of how many disks can be restored is not the whole question.

Let me explain and invite you to tell me where I have made a mistake or not. Let me compare RAID 1+0 and RAID 5 for simplicity.

My question is: given the array has had its first disk failure, what are the odds of rebuilding the replaced disk?

At the time of the first failure, let's say the probability of a disk having a read failure is f.

A RAID 1+0 rebuild relies on 1 other disk being readable. So the odds of rebuilding are (1-f). This is independent of the number of mirror pairs.

A RAID 5 rebuild relies on all the other disks being read successfully (because of the distributed parity algorithm). So the odds of rebuilding are (1-f)^n where n is the number of remaining disks.

So for n>1 the RAID 1+0 array will have better odds of recovery. So this would suggest that a RAID 5 is never a good choice based on data security because when n=1 (a two disk array) the storage capacity is the same as for RAID 1+0.

Based on this reasoning it is not the case that RAID 5 always has the same security as RAID 1+0 even though both have the nominal ability to recover from 1 disk failure.

RAID 6 is a similar story. The maths is more complicated but the outcome is similar. However, the value of n where the odds change over is higher and depends on the value of f. For a typical disk like WD 1TB Caviar Black I use f=8% and get n = 6. This value of f is based on WD's quoted unrecoverable read failure rate of <1 in 10^14 bits read.

Is f=8% too pessimistic? Perhaps when the drives are new. This means on every full read of a 1TB disk you have a 92% chance of no read errors. But once time has passed and one of your disks has failed, I think it would be sensible to assume the other disks are more likely to fail too.

Example:
A 10TB storage capacity RAID 6 (12 disks) vs 10TB capacity RAID 1+0 (20 disks)
f=8% RAID 6 odds of recovering are 78%, RAID 1+0 odds are 92%
f=16% RAID 6 odds 45%, RAID 1+0 odds 84%

Furthermore, it seems to me that RAID 5 and RAID 6 disks will all have similar duty cycles whereas mirror pairs in RAID 1+0 will not because, as I understand it, reading a RAID 1+0 only reads one of the mirrored pairs. This reduces the odds of two mirror pairs both failing at the same time.

> That is true of raid 1+0, but not raid10.  For a 6 disk array, raid6 has a 100% success rate with 1 failure, 100% with 2 failures, and 0% with 3 or more.  raid 1+0 has a 100% success rate with 1 failure, 66% with 2 failures, 33% with 3 failures, 0% with 4+.  The probability of 3 simultaneous failures is much less than 2, so the +33% raid1+0 has in the 3 disk failure case over raid6 does not come close to making up for the -33% success it has in the face of 2 failures.Again, I think the assumption that a RAID 6 has 100% rebuild success rate with 1 disk failure is not right. I really worry because this is the assumption I think most people make. This is what I assumed until I did the maths.


> near + far + offset, not near x far.What you say disagrees with that Wikipedia page. So I'll have to get a 3rd opinion.
But say we have 4 disks and near=4 and far=2 and offset(?)=0. How would the duplicate sectors be arranged?

---

### Post by psusi on 2011-02-18
> **YesWeCan said:**
> 
RAID 6 is a similar story. The maths is more complicated but the outcome is similar. However, the value of n where the odds change over is higher and depends on the value of f. For a typical disk like WD 1TB Caviar Black I use f=8% and get n = 6. This value of f is based on WD's quoted unrecoverable read failure rate of <1 in 10^14 bits read.

Is f=8% too pessimistic? Perhaps when the drives are new. This means on every full read of a 1TB disk you have a 92% chance of no read errors. But once time has passed and one of your disks has failed, I think it would be sensible to assume the other disks are more likely to fail too.

f is WAY too pessimistic.  Usually you talk about whole disk failure, but if you want to look at a single block error rate, an 8% probability would mean people would have bad sectors at least once a week.  That is not anywhere near the case.  The probability of developing a bad sector on any given day is somewhere in the < 1/1000 range.

> **YesWeCan said:**
> 
Example:
A 10TB storage capacity RAID 6 (12 disks) vs 10TB capacity RAID 1+0 (20 disks)
f=8% RAID 6 odds of recovering are 78%, RAID 1+0 odds are 92%
f=16% RAID 6 odds 45%, RAID 1+0 odds 84%

Eventually 1+0 will become more reliable if you use enough disks.  That point may be around the 20 disk mark, I haven't done the math to check.  NOBODY makes arrays that large though.  Raid 1+0 arrays are almost always 4 drives, sometimes 6.  If you want an array that large, instead of 20 disks in 1+0, you do 14 disks and run two 7 disk raid6 arrays.  I'm not sure if at that point which one is more reliable than the other, but the difference is not enough for most people to buy 42% more disks.  The probability of failure with either one is already well below requirements for five nines of uptime.

> **YesWeCan said:**
> Furthermore, it seems to me that RAID 5 and RAID 6 disks will all have similar duty cycles whereas mirror pairs in RAID 1+0 will not because, as I understand it, reading a RAID 1+0 only reads one of the mirrored pairs. This reduces the odds of two mirror pairs both failing at the same time.

The amount of reads are balanced across the paired disks, but even if they weren't, it does not really matter.  It is total run time, and total start/stops that contribute to disk wear, not number of reads.

> **YesWeCan said:**
> Again, I think the assumption that a RAID 6 has 100% rebuild success rate with 1 disk failure is not right. I really worry because this is the assumption I think most people make. This is what I assumed until I did the maths.

Of course it is right.  Any one disk can fail and the data is recomputed from the parity, resulting in no data loss.

> **YesWeCan said:**
> What you say disagrees with that Wikipedia page. So I'll have to get a 3rd opinion.

How so?

> **YesWeCan said:**
> But say we have 4 disks and near=4 and far=2 and offset(?)=0. How would the duplicate sectors be arranged?

Such a setup is not possible.  near=4 and far=2 means 5 duplicate copies, so you need a minimum of 6 disks.  Most people don't use more than 1 duplicate copy, so it is just a question of where?  Near, far, or offset.  You can have both near=2 and far=2 which would look something like this:

```

A    A1    B    B1
C    C1    D    D1
......
B2   D2    A2   C2

```

So you have two duplicate copies of each original data block, where the near one is stored in the next disk in the stripe, and the far one is towards the end of the disks.  This pattern can be generalized to 5, 6, 7, etc disks and can withstand the failure of any 2 disks, since there are 2 duplicate copies of every block.  With 6 disks you only have the space of 2 drives, but can handle two failures, compared to raid 1+0, which gives the space of 3 drives, but can only handle a second failure if it is not in the same mirror as the first.  If you do a 3 way mirrored 1+0, then you get the space and failure modes of the raid10, but the raid10 will have better sequential read throughput.  Specifically you can handle any 2 failures, some combinations of 3 failures, and some combinations of 4 failures.

This is what I think that would look like.  See if you can spot a set of two columns with which you can still reconstruct all data:

```

A    A1    B    B1    C    C1
D    D1    E    E1    F    F1
G    G1    H    H1    I    I1
......
B2   C2    A2   D2    E2   G2
H2   I2    F2

```

---

### Post by YesWeCan on 2011-02-19
> **psusi said:**
> How so?
The article says:
> The near and far options can be used together. The chunks in each section are offset by n device(s). For example n2 f2 layout stores 2×2 = 4 copies of each sector, so requires at least 4 drives:

It says that near = x means there are x copies of each "chunk" across disks and far = y means there are y copies of each chunk along disks. So the total chunks is x times y.

I am not saying you are wrong; just saying that's what Wikipedia says.

I am a little confused that it uses both terms "chunks" and "sectors" so I don't know whether mdadm uses chunks or sectors for RAID 1. I suppose RAID 1 could use either, in theory. I presume "spared out" sectors are invisibly remapped by the disk itself. I suppose mdadm must use chunks for any striping.

---

