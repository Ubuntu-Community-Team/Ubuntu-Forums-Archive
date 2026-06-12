---
title: "Moving a lvm/raid file system to a new machine"
date: 2012-07-31
forum: General Help
---

### Post by hazamatic on 2012-07-31
Hi All,

I currently have a file system running that is made up of 2 mdadm raid5 arrays, and a lvm partition that spans both arrays, and xfs on top of that.

What I want to do is remove all the physical hard drives from this machine, stick them into a new machine, and be able to mount the file system again exactly how it is now.

So what is the best way of doing this? Can I backup my mdadm/lvm configuration and then restore it somehow? I've rebuilt an mdadm array before (manually) but never lvm. 

My current config is below:
# uname -a
Linux helen 3.2.5-030205-generic #201202061401 SMP Mon Feb 6 19:02:31 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid5 sdi1[3] sdh1[1] sdg1[0]
      5860527616 blocks super 1.2 level 5, 128k chunk, algorithm 2 [3/3] [UUU]

md0 : active raid5 sdb1[0] sde1[3] sdd1[2] sdc1[1] sdf1[5]
      3907035136 blocks super 1.2 level 5, 128k chunk, algorithm 2 [5/5] [UUUUU]

unused devices: <none>

# pvdisplay
  --- Physical volume ---
  PV Name               /dev/md1
  VG Name               filesharevg
  PV Size               5.46 TiB / not usable 3.50 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              1430792
  Free PE               0
  Allocated PE          1430792
  PV UUID               lSuE0e-d1FV-seIT-jicJ-7mFq-5te7-fl1Vtb

  --- Physical volume ---
  PV Name               /dev/md0
  VG Name               filesharevg
  PV Size               3.64 TiB / not usable 4.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              953865
  Free PE               0
  Allocated PE          953865
  PV UUID               X99Xj8-WzBt-Aije-2fgz-exgr-4ArG-qtkrZZ

# vgdisplay
  --- Volume group ---
  VG Name               filesharevg
  System ID
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  4
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               9.10 TiB
  PE Size               4.00 MiB
  Total PE              2384657
  Alloc PE / Size       2384657 / 9.10 TiB
  Free  PE / Size       0 / 0
  VG UUID               APKT1k-0GjA-NL9n-s26m-kKVl-cXWi-EscsBb

# lvdisplay
  --- Logical volume ---
  LV Name                /dev/filesharevg/filesharelv
  VG Name                filesharevg
  LV UUID                Wy2sb1-Kigp-Zl9B-yp26-oCpM-fGvh-cLskOM
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                9.10 TiB
  Current LE             2384657
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0

---

### Post by ahallubuntu on 2012-07-31
You can add a snapshot of the logical volume that spans the RAID and then dump the snapshot to a backup file to back it up (to some other drive).  Or use dd, but dump is probably more efficient.

I assume you know how to make a snapshot of an lvm2 partition or can figure that out.  You want to make a snapshot so you aren't dumping active files that could be copied in a corrupted state.

Let's say you make a snapshot and mount it at /mnt/mysnapshot .

Let's say you have an external drive partition mounted at /media/myextdrive .

Then you could do this:

sudo dump -0a -f - /mnt/mysnapshot | gzip -9 > /media/myextdrive/mydump.gz

You can avoid the gzip if the data you'll be copying is already heavily compressed or something.

(for the XFS filesystem, you might look for "xfsdump" instead of "dump," not sure if the original dump command supports XFS directly.)

You could then rebuild the array and restore it from your dumped file.  I have used dump for years including recently on a new Ubuntu 12.04 LTS server with ext4 partitions (LVM but not a RAID) and it works reliably for me; still, you may want to do some experimentation before committing your only copy of your data to this.  I don't know how much data you are taking about, but it's risky to make a backup you're unsure about, wipe out the original, and then try to restore it...

---

### Post by hazamatic on 2012-07-31
Surely there must be a way of doing this without taking a backup of the data.

There is about 7 TiB of data and I don't want to buy 7 TiB  worth of external hard drives to use as a back up...not to mention the time spent making and restoring the backup.

I'd like to just plug in the hard drives into the new machine, run some commands, and have it running it again just like it used to be.

---

### Post by ahallubuntu on 2012-07-31
You probably CAN just plug it in and have it boot on another computer.  I have done that many times, including recently with an LVM (but not a RAID).  I don't know how your RAID is setup exactly, but if you're using a software RAID it may be as simple as just moving the drives.

An LVM isn't tied to any specific hardware.

I was under the impression that you had some need to backup the data before moving it.  I misread what you said about saving the configuration - now I see you meant backing up your configuration, not the data.

---

### Post by hazamatic on 2012-07-31
So I don't need to run pvcreate, vgcreate, etc again? Once I plug the drives in it will detect the existing lvm partition and automatically assemble it?

---

