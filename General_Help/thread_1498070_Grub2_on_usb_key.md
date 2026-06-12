---
title: "Grub2 on usb key"
date: 2010-05-31
forum: General Help
---

### Post by noerbo on 2010-05-31
Hello

I am currently trying to install grub2 on an usb stick.

First i created a partition using fisk.

The usb stick is /dev/sdb

[B][SIZE="4"]fdisk -l /dev/sdb gives:

Disk /dev/sdb: 16.0 GB, 16005464064 bytes
64 heads, 32 sectors/track, 15264 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfafc59fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       15264    15630320   83  Linux[/SIZE][/B]


Then I formatted the partition using [B][I][SIZE="4"]sudo mke2fs -j /dev/sdb1 -L multiBoot
mke2fs 1.41.11 (14-Mar-2010)
Filesystem label=multiBoot
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
977280 inodes, 3907580 blocks
195379 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4001366016
120 block groups
32768 blocks per group, 32768 fragments per group
8144 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: 

This filesystem will be automatically checked every 36 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.[/SIZE][/I][/B]


Then I mounted it as /media/multiBoot


My question is what do I do now? I have tried using

[B][I]sudo grub-install --no-floppy --root-directory=/media/multiBoot/ /dev/sdb
/usr/sbin/grub-setup: warn: Your embedding area is unusually small.  core.img won't fit in it..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.[/I][/B]

Does anyone know what I am doing wrong?[PHP][/PHP]

---

