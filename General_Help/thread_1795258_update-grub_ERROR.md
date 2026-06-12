---
title: "update-grub ERROR"
date: 2011-07-02
forum: General Help
---

### Post by FizzerJE on 2011-07-02
Adding a  kernel parameter to

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nodmraid" (not 100% it should go there grub2 is new to me, but that is another story)

I noticed the following error when running update-grub.

ERROR: ddf1: wrong # of devices in RAID set "ddf1_Series1" [1/2] on /dev/sdb
  No volume groups found



Now I have not a clue where it is getting ddf1_Series1 from.

sdf1 is part of a RAID1 group that has mdadm RAID1 > luks > LVM



md6 : active raid1 sdi1[1] sdf1[0]
      1465135936 blocks [2/2] [UU]
      bitmap: 0/175 pages [0KB], 4096KB chunk


Errors bug me..  as I am new to grub2 was wondering if anyone has an insight into the error / where to investigate

Still reading the grub2  / grub manuals.

---

### Post by FizzerJE on 2011-07-02
Thought that maybe it was becasue the md5 RAID set had a missing drive..
(Managed to break the sata connection to sda, fidding with the cables, since re-soldered a spare connetcor back on the disk, and re-added)

```
cat /proc/mdstat

md6 : active raid1 sdi1[1] sdf1[0]
      1465135936 blocks [2/2] [UU]
      bitmap: 0/175 pages [0KB], 4096KB chunk

md7 : active raid1 sdg1[0] sdh1[1]
      1953511936 blocks [2/2] [UU]
      bitmap: 0/233 pages [0KB], 4096KB chunk

md1 : active raid1 sdd1[1] sde1[0]
      976759343 blocks super 1.2 [2/2] [UU]

md5 : active raid1 sda1[1] sdb1[0]
      976759936 blocks [2/2] [UU]
      bitmap: 1/233 pages [4KB], 2048KB chunk

```



```
mdadm --detail /dev/md5

/dev/md5:
        Version : 0.90
  Creation Time : Fri Mar  5 08:57:12 2010
     Raid Level : raid1
     Array Size : 976759936 (931.51 GiB 1000.20 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 5
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Sat Jul  2 14:51:40 2011
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 70255c32:bd666685:39c31ef3:298efaea
         Events : 0.36273

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8        1        1      active sync   /dev/sda1

```



sdf1 is part of raid set md6


```
mdadm --detail /dev/md6
/dev/md6:
        Version : 0.90
  Creation Time : Tue Jul  6 18:31:05 2010
     Raid Level : raid1
     Array Size : 1465135936 (1397.26 GiB 1500.30 GB)
  Used Dev Size : 1465135936 (1397.26 GiB 1500.30 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 6
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Sat Jul  2 13:39:10 2011
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 91b50e60:45258028:36d0836e:667b33eb
         Events : 0.116626

    Number   Major   Minor   RaidDevice State
       0       8       81        0      active sync   /dev/sdf1
       1       8      129        1      active sync   /dev/sdi1

```



Not understanding the error:

```
ERROR: ddf1: wrong # of devices in RAID set "ddf1_Series1" [1/2] on /dev/sdb

```



Examaning sdf1 and sda1

```
root@taffy:~# mdadm --examine /dev/sdf1
/dev/sdf1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 91b50e60:45258028:36d0836e:667b33eb
  Creation Time : Tue Jul  6 18:31:05 2010
     Raid Level : raid1
  Used Dev Size : 1465135936 (1397.26 GiB 1500.30 GB)
     Array Size : 1465135936 (1397.26 GiB 1500.30 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 6

    Update Time : Sat Jul  2 14:55:37 2011
          State : clean
Internal Bitmap : present
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : eebe5af - correct
         Events : 116626


      Number   Major   Minor   RaidDevice State
this     0       8       81        0      active sync   /dev/sdf1

   0     0       8       81        0      active sync   /dev/sdf1
   1     1       8      129        1      active sync   /dev/sdi1
root@taffy:~# mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 70255c32:bd666685:39c31ef3:298efaea
  Creation Time : Fri Mar  5 08:57:12 2010
     Raid Level : raid1
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 5

    Update Time : Sat Jul  2 14:52:56 2011
          State : clean
Internal Bitmap : present
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : de25f4d - correct
         Events : 36273


      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8        1        1      active sync   /dev/sda1

```


A little confused, but still looking.

---

### Post by dino99 on 2011-07-02
yeah a little confused :(

why do you set grub parameter nodmraid ? you want to use or not use raid ?

to remove: sudo dmraid -rE

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by FizzerJE on 2011-07-03
Thought dmraid was more for psuedo-RAID controllers (onboard, software ones).

Where I am running all software in mdadm.
Always had Disk busy errors, un able to re-add in mdadm, when the dmraid module was loading.

It was a grub kernel parameter I always had to add when I was using CentOS, never had a problem with mdadm and raid after that.

Un-Installing dmraid how-ever, tried that once and it royaly fubar'd me.

I think dmraid takes control of unallocated disks so they appear busy to mdadm, but RAID is all new to me as is GRUB2.

Still learning.

Thanks for link but it is more for dmraid.

---

