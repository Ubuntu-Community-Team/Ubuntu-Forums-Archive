---
title: "Tried LVM on already existing XFS raid6, broke superblock"
date: 2010-05-25
forum: General Help
---

### Post by mihairosu on 2010-05-25
Hey everyone, I hope so badly that this can be fixed as I have so much data on this RAID6 device that I do not want to lose.

Here's basically what happened.

I had a raid device /dev/md2 mounted happily and then I decide I want to play around with lvm.

My plan was to just use my already existing and working raid device and add it to a volume device so I can easily expand this directory at a later date.

I used pvcreate on /dev/md2 and tried to get it working.  I then saw some guides that asked me to create a filesystem on the logical volume and I wasn't sure if that was going to destroy my already existing data.

Now the raid device wouldn't mount on it's own and I assume it was because I created a logical volume ID on it, so I used pvremove -ff /dev/md2 and I hoped that would fix it.

Now when I try xfs_repaid -n /dev/md2 I get the following error:


bad primary superblock - bad magic number !!!

attempting to find secondary superblock...
....................................................................................................
....................................................................................................
....................................................................................................

and this goes on forever.

Am I screwed?

---

### Post by dino99 on 2010-05-25
some help:

[http://unthought.net/Software-RAID.HOWTO/Software-RAID.HOWTO-11.html](http://unthought.net/Software-RAID.HOWTO/Software-RAID.HOWTO-11.html)

[http://stackoverflow.com/questions/237434/raid-verses-lvm](http://stackoverflow.com/questions/237434/raid-verses-lvm)

[http://anthonydawson.thelasis.com/LVRecovery/index.htm](http://anthonydawson.thelasis.com/LVRecovery/index.htm)

[http://www.kernelhardware.org/how-should-run-fsck-linux-file-system/](http://www.kernelhardware.org/how-should-run-fsck-linux-file-system/)

---

### Post by mihairosu on 2010-05-25
Reading through your links, it seems one thing I can do is to just re-create the RAID6 device.  

Here is my output from mdadm --detail /dev/md2

        Version : 00.90
  Creation Time : Sun Jan 17 12:25:12 2010
     Raid Level : raid6
     Array Size : 4395446784 (4191.82 GiB 4500.94 GB)
  Used Dev Size : 732574464 (698.64 GiB 750.16 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Tue May 25 11:43:14 2010
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 32K

           UUID : 3c0308c1:e12f9601:1ef18089:cefb5d8e (local to host ubuntu-nas)
         Events : 0.767699

    Number   Major   Minor   RaidDevice State
       0       8       80        0      active sync   /dev/sdf
       1       8       16        1      active sync   /dev/sdb
       2       8       32        2      active sync   /dev/sdc
       3       8       64        3      active sync   /dev/sde
       4       8        0        4      active sync   /dev/sda
       5       8      112        5      active sync   /dev/sdh
       6       8      128        6      active sync   /dev/sdi
       7       8       96        7      active sync   /dev/sdg


I don't want to possibly make things any worse.  Would that be a good idea?

---

### Post by dino99 on 2010-05-25
the latest link is talking about your problem (fsck)

---

### Post by mihairosu on 2010-05-25
Thanks for the help dino.

Since it's an XFS filesystem I tried to use xfs_check

sudo xfs_check -v /dev/md2 and I get this in return:

xfs_check: /dev/md2 is not a valid XFS filesystem (unexpected SB magic number 0x00000000)
xfs_check: WARNING - filesystem uses v1 dirs,limited functionality provided.
xfs_check: read failed: Invalid argument
xfs_check: data size check failed
cache_node_purge: refcount was 1, not zero (node=0x9cf05b0)
xfs_check: cannot read root inode (22)
bad superblock magic number 0, giving up

Any ideas?

---

### Post by Seq on 2010-05-25
> **mihairosu said:**
> Thanks for the help dino.

Since it's an XFS filesystem I tried to use xfs_check

sudo xfs_check -v /dev/md2 and I get this in return:

xfs_check: /dev/md2 is not a valid XFS filesystem (unexpected SB magic number 0x00000000)
xfs_check: WARNING - filesystem uses v1 dirs,limited functionality provided.
xfs_check: read failed: Invalid argument
xfs_check: data size check failed
cache_node_purge: refcount was 1, not zero (node=0x9cf05b0)
xfs_check: cannot read root inode (22)
bad superblock magic number 0, giving up

Any ideas?

So you had a filesystem on /dev/md2 already, then you overwrote it with a LVM Physical Volume? You're probably pretty screwed.

You'll probably have to start trying recovery programs. The important thing is to **stop using the disk**. I've had luck with [TestDisk and PhotoRec]("http://www.cgsecurity.org") in the past, but they probably won't work with xfs.

A fellow on my LUG has had success with [Foremost]("http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html"). I'm not sure if it can recover from XFS.

---

### Post by mihairosu on 2010-05-25
I didn't realize creating the the LVM Physical Volume would overwrite the existing filesystem.  That will teach me to do things that I don't really understand what they do.

It looks like Testdisk works with XFS and recovers lost partition tables.  

The device is not mounted so nothing should be writing to them.

Thanks Seq, I'll look into using these if no better solution appears and will update this thread with results.

---

### Post by mihairosu on 2010-05-25
SOLVED:  xfs_repair took about 1 hour to run and find a secondary superblock but it was able to repair the array!

Thanks everyone for your help and at the least I learned something about lvm.

---

