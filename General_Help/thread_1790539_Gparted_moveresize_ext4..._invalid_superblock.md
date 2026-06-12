---
title: "Gparted move/resize ext4... invalid superblock"
date: 2011-06-25
forum: General Help
---

### Post by emyr42 on 2011-06-25
I was trying to rearrange my partitions using gparted so that the free space was in a usable place.

I shrank my second partition and clicked apply. It finished successfully.

I then tried to expand my third partition downwards. It sait it would take about 90 minutes, so I went to bed.

When I came back, the screen showed it had stopped in some kind of boot state. I rebooted and found the keyboard didn't work in Xorg. Two cold boots later and it magically worked again.

The expanded partition had not mounted to I loaded gparted up again and got "unable to detect filesystem" on that partition.

> emyr@emyr-desktop:~$ sudo **mke2fs -n /dev/sdb3**
mke2fs 1.41.14 (22-Dec-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
23707648 inodes, 94823304 blocks
4741165 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
2894 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968

emyr@emyr-desktop:~$ 


> emyr@emyr-desktop:~$ sudo **fdisk -l**
[sudo] password for emyr: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x24bf24be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5992    48130708+   7  HPFS/NTFS
/dev/sda2            5993       15722    78156225    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe5f3ed43

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7012    56319952+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2            7208       13582    51200588+  83  Linux
**/dev/sdb3           13582       60801   379293216+  83  Linux**
/dev/sdb4            7012        7207     1570243+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b717b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        6527    52426752    6  FAT16
/dev/sdc2            6528       30401   191767905    0  Empty
emyr@emyr-desktop:~$

I googled a bit and read about backup superblocks, so I tried this:
> emyr@emyr-desktop:~$ sudo** e2fsck -b 163840 /dev/sdb3**
e2fsck 1.41.14 (22-Dec-2010)
e2fsck: Bad magic number in super-block while trying to open /dev/sdb3

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;

emyr@emyr-desktop:~$ 

What should be my next step?

---

