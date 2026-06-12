---
title: "RAID problem after upgrade from Karmic to Lucid"
date: 2010-05-10
forum: General Help
---

### Post by cainscou on 2010-05-10
Hi all,

I recently upgraded from Karmic to Lucid and have been having a problem with my RAID1 array.  My machine has several hard drives and I boot off of a single drive.  My RAID1 is a pair of 750-GB drives housing my photos.

When I boot, Ubuntu hangs on the startup screen telling me that /hammerhead (my RAID mountpoint) cannot be mounted and asks if I want to skip.

When Gnome comes up, I can open the disk utility and it shows a /dev/md0 and a /dev/md_d0 array, both in a partially assembled state.

At this point I run 

```
sudo mdadm -D /dev/md0 
```

and get 

 > mdadm: md device /dev/md0 does not appear to be active.

my /etc/mdadm/mdadm.conf is:

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=9cf9397a:2f777708:99d6da8f:45bb92ea

```

This was made with mkconf

I kill the two RAID arrays in the the Disk utility, and then run blkid to find the block device ids of my individual disks.  Every time I boot, they get reassigned.  Sometimes they are /dev/sde1 and /dev/sdf1, sometimes /dev/sda1 and b1.  It seems completely random.

I then execute:

```
sudo mdadm --create --raid-devices=2 --level=raid1 --assume-clean --run --force /dev/md0 /dev/sdf1 /dev/sde1

sudo mount -t ext4 /dev/md0 /hammerhead


```

and all is well.   The drive mounts and I get 

```
        Version : 00.90
  Creation Time : Mon May 10 19:51:22 2010
     Raid Level : raid1
     Array Size : 732571904 (698.64 GiB 750.15 GB)
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon May 10 19:51:54 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : ec091c32:42fc0daf:fc1ed26f:5fb1723b (local to host squid)
         Events : 0.3

    Number   Major   Minor   RaidDevice State
       0       8       49        0      active sync   /dev/sdd1
       1       8       65        1      active sync   /dev/sde1


```


Note, the UUID of the array that I put in mdadm.conf is the same one reported t me by mdadm on the previous boot.  However when I (or mkconf) put that UUID in my mdadm,conf file, and the do the process above, it assigns a new UUID.

Can anyone tell me:

1. where this /dev/md_d0 array is coming from?
2. why the block device IDs keep shifting?
3. why mdadm keeps assigning different UUIDs?

Any help would be much appreciated.  I've been fighting this problem for over a week, and everything work flawlessly before upgrading.

Thanks,

---

### Post by cainscou on 2010-05-14
FInally figured it out by following this post:

[http://ubuntuforums.org/showthread.php?t=1168360&page=2](http://ubuntuforums.org/showthread.php?t=1168360&page=2)

The key was ```
update-initramfs -u
```


My RAID is still showing up under the wrong UUID under /dev/disk/by-uuid, which messes up fstab unless I call out /dev/md0 implicitly, instead of by UUID.

hopefully this will help someone else.

---

