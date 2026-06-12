---
title: "RAID 5 - MD0 recreated!!"
date: 2011-05-05
forum: General Help
---

### Post by mofirouz on 2011-05-05
Hello. Sorry first time posting here, please bear with me.

Here is my problem. I had installed 10.10 on a NAS server running RAID 5 with Samba. I tried to upgrade to 11.04 and things got really messy and thought I should reinstall everything. So went ahead with the reinstall and now in Ubuntu 11.04 and trying to setup the RAID. First off, it already detected the RAID (But stupid me, ignored that since mates told me!). 

Anyways, so I install mdadm with 5 raid partitions, sda1,sdc1,sdd1,sde1,sdf1 - sdb1 is used as the actual OS, so no backup there.

Now trying to setup up md0 and the mdadm asks me whether I wanted to create a new device. Seeing as how this is a 'virtual' device, I pressed yes and proceeded. Now my array is in 'degraded' mode and 'recovering'. 

I went ahead and changed the fstab file to include the new md0 (which actually to my surprise wasn't included in the fstab already). Then I run:

sudo mount -a 

And it said that it is the 'wrong fs type, bad option, bad superblock on /dev/md0'. 

Now I'm in the middle panicking my a** off because from what I read from the forums, I need to create a new partition on this new device. But I don't wanna do that - because I'll lose everything.

PLEASE PLEASE PLEASE help me with this. There are over 1.7TB of data there and no where else (Family pics, important documents etc etc).

The raid is 8TB and next post will include all the outputs and etc.

THANK YOU in advance

---

### Post by mofirouz on 2011-05-05
OK here we go. All output from relevant commands:

```

 sudo mdadm /dev/md0
/dev/md0: 7452.05GiB raid5 5 devices, 1 spare. Use mdadm --detail for more detail.

``````

sudo mdadm --query --detail /dev/md0
[sudo] password for mo: 
/dev/md0:
        Version : 1.2
  Creation Time : Fri May  6 00:25:04 2011
     Raid Level : raid5
     Array Size : 7814041600 (7452.05 GiB 8001.58 GB)
  Used Dev Size : 1953510400 (1863.01 GiB 2000.39 GB)
   Raid Devices : 5
  Total Devices : 5
    Persistence : Superblock is persistent

    Update Time : Fri May  6 00:25:19 2011
          State : clean, degraded, recovering
 Active Devices : 4
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

 Rebuild Status : 4% complete

           Name : MHF12T:0  (local to host MHF12T)
           UUID : 143e7466:bcb3f2fb:a4892416:c6ef85c5
         Events : 3

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
       5       8       81        4      spare rebuilding   /dev/sdf1


``````

sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

``````

sudo gedit /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=ecb47ea6-d9ef-44d9-8513-cf4224a04f9a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb2 during installation
UUID=02de5cf1-d286-4573-bc24-43616a385609 none            swap    sw              0       0

/dev/md0    /media/raid    ext4    defaults    0    0


```

```

sudo fdisk -l
[sudo] password for mo: 

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5b958351

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      243201  1953512001   fd  Linux RAID autodetect

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14594   117220823+  ee  GPT

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaa4d15d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243201  1953512001   fd  Linux RAID autodetect

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3d011118

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      243201  1953512001   fd  Linux RAID autodetect

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7b8391ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      243201  1953512001   fd  Linux RAID autodetect

Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5775b25a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      243201  1953512001   fd  Linux RAID autodetect

Disk /dev/md0: 8001.6 GB, 8001578598400 bytes
2 heads, 4 sectors/track, 1953510400 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 2097152 bytes
Disk identifier: 0xffffffff

Disk /dev/md0 doesn't contain a valid partition table

```

PLEASE PLEASE help.

Thank you :)

---

### Post by mofirouz on 2011-05-05
The question that remains is that, does formatting md0 to ext4 (again) would remove ALL my data from the array?

PLEASE help someone!

---

### Post by bDerrly on 2011-05-05
> **mofirouz said:**
> The question that remains is that, does formatting md0 to ext4 (again) would remove ALL my data from the array?

PLEASE help someone!

Yes. that will erase all of your data.

---

### Post by mofirouz on 2011-05-06
Thanks for the reply... so how would I go about getting my data back? Cuz I can't mound the disks because md0 doesn't have a partition....

Have I already lost all my data?

---

### Post by mofirouz on 2011-05-06
Don't matter now....

*I call Multi-Disk, md0*

I had done a bit of reading, and the actual file structure is saved on the md0, even though that is a 'virtual' drive. So once md0 is over-written, with a new md0 your file structure is actually lost.

This is regardless of the fact that you have the superblocks on each array partition. This is because the arrays themselves don't have any partition type and therefore you cannot actually grab anything back from the data once the file system is lost.

2TB of data, just lost. *Sigh*

Good luck with anyone finding this post in the future.
Mo.

---

