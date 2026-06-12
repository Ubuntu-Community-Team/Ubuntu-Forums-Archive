---
title: "micro sd card cannot be formatted in ext3, but fat32 is OK"
date: 2012-02-25
forum: General Help
---

### Post by Sredni Vasthar on 2012-02-25
Hi,

I am trying to create two partitions on my 8G scandisk microsd card - one is a FAT32 and the other one is ext3, using ubuntu oneric. I need this for it to act as a boot disk for my Beagle Board. I have checked lots of posts and am basically following the instructions at:
[http://elinux.org/BeagleBoardBeginners#SD_card_setup](http://elinux.org/BeagleBoardBeginners#SD_card_setup)
But no matter what I do, the creation of ext3 file system always fails.
sudo mkfs.ext3 does not seem to work properly. I am never able to mount 
the ext3 partition, I always get an error saying "unable to mount could be a bad bock
or superblock or bad file system ... etc"

So then I tried using Gparted to format the whole drive as FAT32. that works. 
But if I try to format the whole drive as ext3, gparted reports an error at 
the file system creation stage.
[SIZE=2]create new ext3 file system  00:00:05    ( ERROR ) [/SIZE]            [SIZE=1]***mkfs.ext3 -L "" /dev/mmcblk0p1***[/SIZE]         [SIZE=1][I]Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
32768 inodes, 131072 blocks
6553 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=134217728
4 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
    32768, 98304

Writing inode tables: done                            
Creating journal (4096 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 27 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
[/I][/SIZE]       [I][SIZE=1]mke2fs 1.41.14 (22-Dec-2010)[/SIZE]
[SIZE=1]
Warning, had trouble writing out superblocks.[/SIZE][/I]I then tried various size ext3 partitions using Gparted, it does not work either.
But FAT32 is perfect..

Any ideas what could be wrong??

---

### Post by dcstar on 2012-02-26
> **Sredni Vasthar said:**
> 
.........
Any ideas what could be wrong??

Use gparted to write a new Partition Table and try again.

---

### Post by Sredni Vasthar on 2012-03-04
Hi Dave,  Thanks a lot for your reply, I just saw it now. Well I tried Creating a new msdos and gpt partition table using gparted, and I tried formatting the entire SD card in ext3; but even that is not possible. Gparted always fails when creating the file system..  Is it possible that the SD card does not support ext3, but FAT is ok?   Meanwhile i bought another sd card (not scandisk) for the beagle, and that works fine..  Govind

---

