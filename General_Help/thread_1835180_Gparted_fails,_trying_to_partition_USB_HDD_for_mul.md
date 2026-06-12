---
title: "Gparted fails, trying to partition USB HDD for multi-boot"
date: 2011-08-28
forum: General Help
---

### Post by Singtoh on 2011-08-28
Hello All,

I am having a problem partitioning an external HDD for a multiboot using Gparted. I am using a Ubuntu 10.10 64bit Live CD on a USB thumb drive to try to partition a 120gig USB HDD into 8gig for /, and 2gig for /home. I repeat this pattern until I near the end of the drive, then the last few gig I make into a few small fat32 partitions and then on the end of the drive I put  a swap area. I have installed up to 6 distros on these drives one by one and it seems to boot into all of them without a problem, but I would rather partition the whole drive before starting to install distro's. I would like to end up with a USB HDD that can have 9 or 10 different distros on it to play around with, but it always seems to fail after making about 10 to 12 partitions, or sometimes even fails straight away after 2 or 3 partitions. The first thing I do is make the whole HDD into an extended partition, then all other partitions made are of course Logical partitions. I have tried this on 3 different external USB HDD'S and get roughly the same result but it is always a different partition that makes it fail. All of these drives are under 1 year old, smart status is always good with no errors. Am I missing something here?? I thought I could make as many logical partitions as I wanted to?? Below is the error report:

GParted 0.6.2

Libparted 2.3
Create Logical Partition #1 (ext4, 7.81 GiB) on /dev/sdd  00:00:11    ( SUCCESS )
     	
create empty partition  00:00:01    ( SUCCESS )
     	
path: /dev/sdd5
start: 4096
end: 16388095
size: 16384000 (7.81 GiB)
set partition type on /dev/sdd5  00:00:00    ( SUCCESS )
     	
new partition type: ext4
create new ext4 file system  00:00:10    ( SUCCESS )
     	
mkfs.ext4 -j -O extent -L "" /dev/sdd5
     	
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
512064 inodes, 2048000 blocks
102400 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=2097152000
63 block groups
32768 blocks per group, 32768 fragments per group
8128 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 31 mounts or
180 days, whichever comes first. Use tune2fs -c or -i to override.
mke2fs 1.41.12 (17-May-2010)

========================================
Create Logical Partition #2 (ext4, 1.95 GiB) on /dev/sdd  00:00:04    ( SUCCESS )
     	
create empty partition  00:00:01    ( SUCCESS )
     	
path: /dev/sdd6
start: 16390144
end: 20486143
size: 4096000 (1.95 GiB)
set partition type on /dev/sdd6  00:00:00    ( SUCCESS )
     	
new partition type: ext4
create new ext4 file system  00:00:03    ( SUCCESS )
     	
mkfs.ext4 -j -O extent -L "" /dev/sdd6
     	
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
128000 inodes, 512000 blocks
25600 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=524288000
16 block groups
32768 blocks per group, 32768 fragments per group
8000 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912

Writing inode tables: done
Creating journal (8192 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 32 mounts or
180 days, whichever comes first. Use tune2fs -c or -i to override.
mke2fs 1.41.12 (17-May-2010)

========================================
Create Logical Partition #3 (ext4, 7.81 GiB) on /dev/sdd  00:00:12    ( SUCCESS )
     	
create empty partition  00:00:01    ( SUCCESS )
     	
path: /dev/sdd7
start: 20488192
end: 36872191
size: 16384000 (7.81 GiB)
set partition type on /dev/sdd7  00:00:01    ( SUCCESS )
     	
new partition type: ext4
create new ext4 file system  00:00:10    ( SUCCESS )
     	
mkfs.ext4 -j -O extent -L "" /dev/sdd7
     	
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
512064 inodes, 2048000 blocks
102400 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=2097152000
63 block groups
32768 blocks per group, 32768 fragments per group
8128 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 35 mounts or
180 days, whichever comes first. Use tune2fs -c or -i to override.
mke2fs 1.41.12 (17-May-2010)

========================================
Create Logical Partition #4 (ext4, 1.95 GiB) on /dev/sdd  00:00:04    ( SUCCESS )
     	
create empty partition  00:00:01    ( SUCCESS )
     	
path: /dev/sdd8
start: 36874240
end: 40970239
size: 4096000 (1.95 GiB)
set partition type on /dev/sdd8  00:00:01    ( SUCCESS )
     	
new partition type: ext4
create new ext4 file system  00:00:02    ( SUCCESS )
     	
mkfs.ext4 -j -O extent -L "" /dev/sdd8
     	
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
128000 inodes, 512000 blocks
25600 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=524288000
16 block groups
32768 blocks per group, 32768 fragments per group
8000 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912

Writing inode tables: done
Creating journal (8192 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 24 mounts or
180 days, whichever comes first. Use tune2fs -c or -i to override.
mke2fs 1.41.12 (17-May-2010)

========================================
Create Logical Partition #5 (ext4, 7.81 GiB) on /dev/sdd  00:00:13    ( SUCCESS )
     	
create empty partition  00:00:02    ( SUCCESS )
     	
path: /dev/sdd9
start: 40972288
end: 57356287
size: 16384000 (7.81 GiB)
set partition type on /dev/sdd9  00:00:01    ( SUCCESS )
     	
new partition type: ext4
create new ext4 file system  00:00:10    ( SUCCESS )
     	
mkfs.ext4 -j -O extent -L "" /dev/sdd9
     	
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
512064 inodes, 2048000 blocks
102400 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=2097152000
63 block groups
32768 blocks per group, 32768 fragments per group
8128 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 33 mounts or
180 days, whichever comes first. Use tune2fs -c or -i to override.
mke2fs 1.41.12 (17-May-2010)

========================================
Create Logical Partition #6 (ext4, 1.95 GiB) on /dev/sdd  00:00:05    ( SUCCESS )
     	
create empty partition  00:00:01    ( SUCCESS )
     	
path: /dev/sdd10
start: 57358336
end: 61454335
size: 4096000 (1.95 GiB)
set partition type on /dev/sdd10  00:00:01    ( SUCCESS )
     	
new partition type: ext4
create new ext4 file system  00:00:03    ( SUCCESS )
     	
mkfs.ext4 -j -O extent -L "" /dev/sdd10
     	
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
128000 inodes, 512000 blocks
25600 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=524288000
16 block groups
32768 blocks per group, 32768 fragments per group
8000 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912

Writing inode tables: done
Creating journal (8192 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 26 mounts or
180 days, whichever comes first. Use tune2fs -c or -i to override.
mke2fs 1.41.12 (17-May-2010)

========================================
Create Logical Partition #7 (ext4, 7.81 GiB) on /dev/sdd  00:00:14    ( SUCCESS )
     	
create empty partition  00:00:02    ( SUCCESS )
     	
path: /dev/sdd11
start: 61456384
end: 77840383
size: 16384000 (7.81 GiB)
set partition type on /dev/sdd11  00:00:01    ( SUCCESS )
     	
new partition type: ext4
create new ext4 file system  00:00:11    ( SUCCESS )
     	
mkfs.ext4 -j -O extent -L "" /dev/sdd11
     	
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
512064 inodes, 2048000 blocks
102400 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=2097152000
63 block groups
32768 blocks per group, 32768 fragments per group
8128 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 30 mounts or
180 days, whichever comes first. Use tune2fs -c or -i to override.
mke2fs 1.41.12 (17-May-2010)

========================================
Create Logical Partition #8 (ext4, 1.95 GiB) on /dev/sdd  00:00:06    ( SUCCESS )
     	
create empty partition  00:00:02    ( SUCCESS )
     	
path: /dev/sdd12
start: 77842432
end: 81938431
size: 4096000 (1.95 GiB)
set partition type on /dev/sdd12  00:00:01    ( SUCCESS )
     	
new partition type: ext4
create new ext4 file system  00:00:03    ( SUCCESS )
     	
mkfs.ext4 -j -O extent -L "" /dev/sdd12
     	
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
128000 inodes, 512000 blocks
25600 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=524288000
16 block groups
32768 blocks per group, 32768 fragments per group
8000 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912

Writing inode tables: done
Creating journal (8192 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 24 mounts or
180 days, whichever comes first. Use tune2fs -c or -i to override.
mke2fs 1.41.12 (17-May-2010)

========================================
Create Logical Partition #9 (ext4, 7.81 GiB) on /dev/sdd  00:00:14    ( SUCCESS )
     	
create empty partition  00:00:02    ( SUCCESS )
     	
path: /dev/sdd13
start: 81940480
end: 98324479
size: 16384000 (7.81 GiB)
set partition type on /dev/sdd13  00:00:02    ( SUCCESS )
     	
new partition type: ext4
create new ext4 file system  00:00:10    ( SUCCESS )
     	
mkfs.ext4 -j -O extent -L "" /dev/sdd13
     	
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
512064 inodes, 2048000 blocks
102400 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=2097152000
63 block groups
32768 blocks per group, 32768 fragments per group
8128 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 20 mounts or
180 days, whichever comes first. Use tune2fs -c or -i to override.
mke2fs 1.41.12 (17-May-2010)

========================================
Create Logical Partition #10 (ext4, 1.95 GiB) on /dev/sdd  00:00:07    ( SUCCESS )
     	
create empty partition  00:00:02    ( SUCCESS )
     	
path: /dev/sdd14
start: 98326528
end: 102422527
size: 4096000 (1.95 GiB)
set partition type on /dev/sdd14  00:00:02    ( SUCCESS )
     	
new partition type: ext4
create new ext4 file system  00:00:03    ( SUCCESS )
     	
mkfs.ext4 -j -O extent -L "" /dev/sdd14
     	
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
128000 inodes, 512000 blocks
25600 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=524288000
16 block groups
32768 blocks per group, 32768 fragments per group
8000 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912

Writing inode tables: done
Creating journal (8192 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 22 mounts or
180 days, whichever comes first. Use tune2fs -c or -i to override.
mke2fs 1.41.12 (17-May-2010)

========================================
Create Logical Partition #11 (ext4, 7.81 GiB) on /dev/sdd  00:00:16    ( SUCCESS )
     	
create empty partition  00:00:03    ( SUCCESS )
     	
path: /dev/sdd15
start: 102424576
end: 118808575
size: 16384000 (7.81 GiB)
set partition type on /dev/sdd15  00:00:03    ( SUCCESS )
     	
new partition type: ext4
create new ext4 file system  00:00:10    ( SUCCESS )
     	
mkfs.ext4 -j -O extent -L "" /dev/sdd15
     	
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
512064 inodes, 2048000 blocks
102400 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=2097152000
63 block groups
32768 blocks per group, 32768 fragments per group
8128 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 29 mounts or
180 days, whichever comes first. Use tune2fs -c or -i to override.
mke2fs 1.41.12 (17-May-2010)

========================================
Create Logical Partition #12 (ext4, 1.95 GiB) on /dev/sdd  00:00:09    ( SUCCESS )
     	
create empty partition  00:00:03    ( SUCCESS )
     	
path: /dev/sdd16
start: 118810624
end: 122906623
size: 4096000 (1.95 GiB)
set partition type on /dev/sdd16  00:00:03    ( SUCCESS )
     	
new partition type: ext4
create new ext4 file system  00:00:03    ( SUCCESS )
     	
mkfs.ext4 -j -O extent -L "" /dev/sdd16
     	
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
128000 inodes, 512000 blocks
25600 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=524288000
16 block groups
32768 blocks per group, 32768 fragments per group
8000 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912

Writing inode tables: done
Creating journal (8192 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 35 mounts or
180 days, whichever comes first. Use tune2fs -c or -i to override.
mke2fs 1.41.12 (17-May-2010)

========================================
Create Logical Partition #13 (ext4, 7.81 GiB) on /dev/sdd  00:00:07    ( ERROR )
     	
create empty partition  00:00:03    ( SUCCESS )
     	
path: /dev/sdd17
start: 122908672
end: 139292671
size: 16384000 (7.81 GiB)
set partition type on /dev/sdd17  00:00:04    ( SUCCESS )
     	
new partition type: ext4
create new ext4 file system  00:00:00    ( ERROR )
     	
mkfs.ext4 -j -O extent -L "" /dev/sdd17
     	
mke2fs 1.41.12 (17-May-2010)
Could not stat /dev/sdd17 --- No such file or directory

The device apparently does not exist; did you specify it correctly?

========================================
Create Logical Partition #14 (ext4, 1.95 GiB) on /dev/sdd

========================================
Create Logical Partition #15 (ext4, 7.81 GiB) on /dev/sdd

========================================
Create Logical Partition #16 (ext4, 1.95 GiB) on /dev/sdd

========================================
Create Logical Partition #17 (ext4, 7.81 GiB) on /dev/sdd

========================================
Create Logical Partition #18 (ext4, 1.95 GiB) on /dev/sdd

========================================
Create Logical Partition #19 (ext4, 7.81 GiB) on /dev/sdd

========================================
Create Logical Partition #20 (ext4, 1.95 GiB) on /dev/sdd

========================================
Create Logical Partition #21 (ext4, 9.77 GiB) on /dev/sdd

========================================
Create Logical Partition #22 (fat32, 1000.00 MiB) on /dev/sdd

========================================
Create Logical Partition #23 (fat32, 1000.00 MiB) on /dev/sdd

========================================
Create Logical Partition #24 (fat32, 1000.00 MiB) on /dev/sdd

========================================
Create Logical Partition #25 (linux-swap, 1.41 GiB) on /dev/sdd

========================================

I hope I am not being daft here and missing something obvious. I thank you in advance for any advice or help on this issue.

Cheers,

Singtoh

---

