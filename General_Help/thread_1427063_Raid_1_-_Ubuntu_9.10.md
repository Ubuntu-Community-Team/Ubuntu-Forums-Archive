---
title: "Raid 1 - Ubuntu 9.10"
date: 2010-03-11
forum: General Help
---

### Post by peter.cyr on 2010-03-11
I recently overhauled my home server and setup 2 raid 1 arrays.

I set it up with 2x1TB and 2x1.5TB

I used the Palimpsest tool that comes with Ubuntu to create the arrays. The problem is every time I reboot, the arrays aren't mounted to where they should be, and they don't come up as the right device.

/dev/md0 is supposed to be /dev/sdb1 and /dev/sde1
/dev/md1 is supposed to be /dev/sdc1 and /dev/sdd1

Upon reboot, they come up as /dev/md126 and /dev/md127 ??

If I do mdadm --stop --scan and I restart them individually in the Palimsest tool, they come up fine and mount to the right mount points (/mnt/storage and /mnt/media)

Here's the output of the related files.

/etc/mdadm/mdadm.conf

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


# This file was auto-generated on Mon, 08 Mar 2010 21:35:09 -0400
# by mkconf $Id$
ARRAY /dev/md/Media level=raid1 metadata=1.2 num-devices=2 UUID=dcf5188b:792de46d:931b8268:b72788ae name=:Media
ARRAY /dev/md/Storage level=raid1 metadata=1.2 num-devices=2 UUID=6e01e61e:e41520d0:0da4cc10:1fcd05f0 name=:Storage


/etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=94b2362d-28ef-47ca-82f8-42c732f40921 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=eb579a12-ee70-4629-b525-622a58e13e30 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
UUID="75ebfe37-d893-41a0-9504-8c11018fa517" /mnt/storage ext4 defaults 0 0
UUID="851cf25c-e96e-4680-8880-18ee8adb161f" /mnt/media ext4 defaults 0 0 

And here's the output of mdadm --examine for each device in each array.

for the 2 drives in /etc/md0

/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 6e01e61e:e41520d0:0da4cc10:1fcd05f0
           Name : :Storage
  Creation Time : Fri Mar  5 04:20:45 2010
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 1953519730 (931.51 GiB 1000.20 GB)
     Array Size : 1953519730 (931.51 GiB 1000.20 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : fdf7e97f:3a336d07:1ce5d8fa:673469d8

    Update Time : Thu Mar 11 03:13:54 2010
       Checksum : 4883e4d7 - correct
         Events : 2400


    Array Slot : 1 (0, 1)
   Array State : uU

dev/sde1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 6e01e61e:e41520d0:0da4cc10:1fcd05f0
           Name : :Storage
  Creation Time : Fri Mar  5 04:20:45 2010
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 1953519730 (931.51 GiB 1000.20 GB)
     Array Size : 1953519730 (931.51 GiB 1000.20 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 5f0aad38:f222fde3:72e1e99e:c3bd6c3d

    Update Time : Thu Mar 11 03:13:54 2010
       Checksum : e6eb6ca1 - correct
         Events : 2400


    Array Slot : 0 (0, 1)
   Array State : Uu

for the 2 drives in /etc/md1

/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : dcf5188b:792de46d:931b8268:b72788ae
           Name : :Media
  Creation Time : Mon Mar  8 21:58:56 2010
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 2930271730 (1397.26 GiB 1500.30 GB)
     Array Size : 2930271730 (1397.26 GiB 1500.30 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : d8be91c6:e40ef8af:69b898da:4742bf43

    Update Time : Thu Mar 11 03:14:07 2010
       Checksum : a6fa3f05 - correct
         Events : 52


    Array Slot : 1 (0, 1)
   Array State : uU

/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : dcf5188b:792de46d:931b8268:b72788ae
           Name : :Media
  Creation Time : Mon Mar  8 21:58:56 2010
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 2930271730 (1397.26 GiB 1500.30 GB)
     Array Size : 2930271730 (1397.26 GiB 1500.30 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : ca4ed7fd:842738a8:d289c163:e876dbaa

    Update Time : Thu Mar 11 03:14:07 2010
       Checksum : c6c4eda0 - correct
         Events : 52


    Array Slot : 0 (0, 1)
   Array State : Uu


Can anyone shed some light on this? And it seems like if I reboot without manually unmounting them and stopping them, i'm stuck having to rebuild the arrays upon reboot for some reason. With the size of those arrays, takes for ever.

I'm not 100% clueless when it comes to linux but i'm starting to get the feeling i'm not far from. haha.

Thanks in advance

---

