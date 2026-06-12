---
title: "trying to recover files from a maxtor drive"
date: 2011-05-07
forum: General Help
---

### Post by eric.ooly on 2011-05-07
I have the hard drive (1 TB) ext3 (I think) formatted drive that was in a maxtor central axis server that broke. I am pretty sure the drive is OK, and it was the Maxtor part that was bad.   I booted a pc with ubuntu on a thumb drive, with this hard drive installed.

I ran sudo lshw -C disk to see if the drive is there.

It is, with logical name: /dev/sda
description : SCSI Disk

I want to mount this drive and try to recover the files by copying them.

How do I mount the drive?  and explore the file structure

---

### Post by doas777 on 2011-05-07
first I would check the smart data on the drive with Disk Utility before proceeding. if the drive is failing, you want to image it immediately, if it is possible. 

if the smart data looks good, you could mount it with defaults with
```
sudo mkdir /media/sda1
sudo mount /dev/sda1 /media/sda1
```and see if it comes up as is.

as for actual data recovery, here is a good coverage of the basics:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

if you find you need to image the drive, I recommend ddrescue.

---

### Post by 73ckn797 on 2011-05-07
You may want to enter in terminal:
```
sudo mount /dev/sda /mnt
```

Or read this: [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

---

### Post by eric.ooly on 2011-05-07
Making progress.....The hard drive is good (it was the maxtor server that was bad)  In disk utility I see the drive, it has 6 volumes, /dev/sda1 though /dev/sda6.  all the partition types come up as unknown, and so I had trouble with the mounting because it says I need to specify the filesystem type.  I found a post that says these drive are stored in linux format, as ext3 partitions.

---

### Post by doas777 on 2011-05-07
please post the output of 
```
sudo fdisk -l
```

---

### Post by eric.ooly on 2011-05-07
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         488     3919841    b  W95 FAT32
ubuntu@ubuntu:~$ 


as you see, this does not see the /dev/sda drive, but it does come up in _disk utility_ as 1.0 TB Hard Disk
ATA ST31000340AS

---

### Post by doas777 on 2011-05-07
does it show the partition type in parted?

```
sudo parted -l
```

---

### Post by eric.ooly on 2011-05-07
no, I get an unrecognised disk label error.  Here it is :

ubuntu@ubuntu:~$ sudo parted -l
Error: /dev/sda: unrecognised disk label                                  

Model: SanDisk SanDisk Cruzer (scsi)
Disk /dev/sdb: 4022MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      19.5kB  4014MB  4014MB  primary  fat32        boot


Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.
Error: /dev/sr1: unrecognised disk label

---

### Post by doas777 on 2011-05-07
your NAS supported a few raid types. do you recall whether/which raid you were using?

here is the admin guide, btw:[http://www.seagate.com/staticfiles/support/central_axis/Maxtor%20Central%20Axis%20Admin%20User%20Guide.pdf](http://www.seagate.com/staticfiles/support/central_axis/Maxtor%20Central%20Axis%20Admin%20User%20Guide.pdf)

---

### Post by eric.ooly on 2011-05-07
I got this from someone posting how to do this in windows :

Inside the Central Axis is a simple Seagate Barracuda 7200 RPM SATA drive. The server runs an embedded form of Linux, so the drive is formatted with an EXT3 partition. Although Windows can’t natively mount this format, there are utilities that can.

I don't this this used raid as there was only one hard disk in the device.

under windows he reccomended to do this using :

Explore2fs, the WIN32 explorer for Linux ext2fs partitions

I am trying to do this under ubuntu because in order to access this hard drive, I had to use the cable from the windows hard drive and boot the computer with my ubuntu flash drive.  And also I am trying to get better at doing stuff in ubuntu.

---

### Post by doas777 on 2011-05-07
I think the issue at this point is that the partition table type is unknown, regardless of the filesystem types of the individual volumes. the document doesn't really state the file system type either, which is a little worrysome. since you say raid has never come up, I assume you are using a single disk nas. is this correct?

---

### Post by eric.ooly on 2011-05-07
Any idea on how to specify the file system type, and the types of filesystems there are?

Here's the error :

ubuntu@ubuntu:~$ sudo mkdir /media/sda6
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /media/sda6
mount: you must specify the filesystem type

---

### Post by eric.ooly on 2011-05-07
yes, this was a very cheap and simple product.  Just a single 1 TB hard drive connected to the network.

---

### Post by doas777 on 2011-05-07
if you open up GParted, does it show a partition table?
booting from a testdisk live cd may also be albe to detect the partition type.

---

### Post by eric.ooly on 2011-05-07
I don't know if this helps, but I found this info an a similar product from Maxtor, except this one had 2 disk drives.  The sizes of the six partitions is very much like what I have on my one drive, so I would guess they set these up the same way.  It looks like the data I want to recover is in sda6

Disk configuration

The Red cable connects to /dev/sda, the Blue cable connects to /dev/sdb.
Internal disks are partitioned and formatted as shown below (only the size of /dev/sda6 will be different for other size disks):

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
 
   Device Boot  Start    End     Blocks   Id  System 
/dev/sda1   *       1     32     257008+  83  Linux 
/dev/sda2          33     64     257040   83  Linux 
/dev/sda3          65     96     257040   82  Linux swap / Solaris 
/dev/sda4          97  91201  731800912+   5  Extended 
/dev/sda5          97    159     506016   83  Linux 
/dev/sda6         160  91201  731294833+  83  Linux 
The following functionality is provided by the partitions:

/dev/sda1 (SYS1) - 256MB boot partition
/dev/sda2 (SYS2) - 256MB boot partition (backup)
/dev/sda3 (SWAP) - 256MB swap partition
/dev/sda5 (Tmp) - 512MB tmp partition
/dev/sda6 (DATA) - data partition
Use the fdisk /dev/sda command to partition the disk. Format the partition as follows:

mkswap /dev/sda3
mkfs.ext3 -j -b 4096 /dev/sda1
mkfs.ext3 -j -b 4096 /dev/sda2
mkfs.ext3 -j -b 4096 /dev/sda5
mkfs.ext3 -j -b 4096 -m 0 /dev/sda6

---

### Post by eric.ooly on 2011-05-07
no gparted does not see it.  I'll try booting from a ubuntu 10.04 and see if that's better.   Thanks for all your help!

---

### Post by tgalati4 on 2011-05-08
Because the drive does not have a properly formatted partition table, Ubuntu/linux tools may have some difficulty.

sudo mkdir /media/helpmerecoverthisdisk
sudo mount -t ext3 /dev/sda1 /media/helpmerecoverthisdisk

This is not a fun way to learn linux.

I would put the drive into a machine with linux installed and it will be much easier to recover than trying to use a live CD/USB stick.  Better yet, find a local linux user group (lug) in your town and bring the disk (wrapped in a towel for dramatic effect) and let them work the "magic".

---

