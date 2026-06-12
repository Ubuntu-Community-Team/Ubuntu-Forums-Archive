---
title: "mdadm: No md superblock detected"
date: 2009-09-01
forum: General Help
---

### Post by TC1 on 2009-09-01
Hello.  I have (had?) a RAID1 array that has a superblock issue after a power outage/reboot.  I've tried reassembling, recreating the mdadm.conf, and everything else I can think of.  I don't want to lose the data that's on there, but I've run into a wall.

Here is the output of various commands:
~$ sudo mount /dev/md0 /media/sharedfiles
mount: you must specify the filesystem type


~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Wed Jun 17 12:36:51 2009
     Raid Level : raid1
     Array Size : 488383936 (465.76 GiB 500.11 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Sep  1 17:17:39 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 6161bfd5:75dad181:c8678b8d:95f6e41b (local to host tcl)
         Events : 0.30

    Number   Major   Minor   RaidDevice State
       0       8        4        0      active sync   /dev/sda4
       1       8       17        1      active sync   /dev/sdb1


~$ sudo mdadm -E /dev/md0
mdadm: No md superblock detected on /dev/md0.


It's obviously something with the superblock, but my n00b self can't seem to figure out how to fix it!  Any help would be much appreciated!

---

### Post by denver on 2009-09-01
Might be a long shot, but seeing as its a RAID1, you can try to mount eather one of the disks inside md0 as a separate disk. RAID1 replicates the same data across disks so if you remove one of the disks from the array, you might be able to mount it an recover any critical data. 

Also, you might want to run a fsck on the array to fix any FileSystem inconsistencies. Hope this is of some use to you.

Good luck!

EDIT: the --examine option is usualy used on a member of the array, not the array itself

---

### Post by TC1 on 2009-09-02
Thanks for the tips, but when I try to mount the disks directly it tells me it can't find they  filesystem.  I also tried fsck with all the backup superblocks, and they all have a mismatch with the number of blocks.

At this point, I'd appreciate anything!  I've been googling for hours and can't find anything that works.  I don't have the space for a backup, and I don't want to lose the data!

---

### Post by TC1 on 2009-09-02
Sorry for the bump, but does anyone have any recommendations?

---

### Post by tgrimley on 2009-09-02
> ~$ sudo mount /dev/md0 /media/sharedfiles
mount: you must specify the filesystem type

Did you try specifying the filesystem type? ext2, xfs, whatever?

> ~$ sudo mdadm -E /dev/md0
run -E on each partition in the array see if one is marked as failed

---

### Post by denver on 2009-09-03
Also try the following command:

```
vol_id /dev/md0
```

and see what that prints out. You should see some information about the filesystem on that particular volume.

---

### Post by TC1 on 2009-09-03
```
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 6161bfd5:75dad181:c8678b8d:95f6e41b (local to host tcl)
  Creation Time : Wed Jun 17 12:36:51 2009
     Raid Level : raid1
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Wed Sep  2 00:30:02 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 90b9871e - correct
         Events : 30


      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8        4        0      active sync   /dev/sda4
   1     1       8       17        1      active sync   /dev/sdb1

```
```

 sudo mdadm -E /dev/sda4
/dev/sda4:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 6161bfd5:75dad181:c8678b8d:95f6e41b (local to host tcl)
  Creation Time : Wed Jun 17 12:36:51 2009
     Raid Level : raid1
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Wed Sep  2 00:30:02 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 90b9870f - correct
         Events : 30


      Number   Major   Minor   RaidDevice State
this     0       8        4        0      active sync   /dev/sda4

   0     0       8        4        0      active sync   /dev/sda4
   1     1       8       17        1      active sync   /dev/sdb1

```


For the vol_id:
```

:~$ sudo vol_id /dev/md0
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext4
ID_FS_VERSION=1.0
ID_FS_UUID=165aefe3-bb4c-4bab-8115-8fa14f74825f
ID_FS_UUID_ENC=165aefe3-bb4c-4bab-8115-8fa14f74825f
ID_FS_LABEL=
ID_FS_LABEL_ENC=

```

Trying to force the filesystem, I get:
```

~$ sudo mount -t ext4 /dev/md0 /media/sharedfiles
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

This messed up superblock is killing me.... any pointers on how to fix it without wiping the data?

---

### Post by denver on 2009-09-03
Not really sure what the problem might be. As the error message suggests, you might find out more info by doing a:

```
dmesg | tail 
```

after the mount command. The ext4 filesystem was first supported in Jaunty, so make sure you are not using an earlyer version of Ubuntu.

If you suspect it might be the superblock that's giving you these headaches, you can also try this:

[http://blog.edseek.com/archives/2004/02/25/ext3-filesystem-bad-superblock-recovery/](http://blog.edseek.com/archives/2004/02/25/ext3-filesystem-bad-superblock-recovery/)

This guide also shows how to use a backup superblock with the mount command. Hope this helps, I'm fresh out of ideeas.

Good luck!

---

### Post by badcmpy on 2009-09-18
I also had a similar problem with my RAID 1. After a few weeks of searching I had found several threads on the topic and what worked for me was to simply add '-U super-minor' to my assemble command for mdadm. Even though the error says bad superblock this fixed my problems.

One thread I read blamed the hardware SATA/RAID controller that I have for causing the problems although I'm not sure how much truth is there.

Try something like this:

mdadm -A /dev/md0 -U super-minor



On second thought this might not be your problem because mine always had the partition checksums out of wack although yours look good.

---

