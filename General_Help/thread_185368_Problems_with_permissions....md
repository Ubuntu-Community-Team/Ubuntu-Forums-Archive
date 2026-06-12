---
title: "Problems with permissions..."
date: 2006-05-31
forum: General Help
---

### Post by Core407 on 2006-05-31
Linux n00b here trying out something new after getting bored with XP. I've ran into a couple of problems, but my main one right now is with permissions.

Basically I'm trying to transfer some stuff from 1 HDD to another, but I don't have write permission. When I right click on the drive, hit properties and check out permissions, everything is greyed out (unclickable). I'm guessing it's because I don't have the clearance to do a change like that. So I've gone itno system > users and it says I'm capable of doing it, but the folder just won't allow me. Any ideas?

---

### Post by aysiu on 2006-05-31
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by bullgr on 2006-05-31
if the disk is formated in ntfs format then forget it...
ntfs is read-only in linux, some steps are done to support read-write
but it's risky for the moment.

if the disk is not ntfs, then open a terminal and write
> sudo chmod -R 777 /mnt/d
to change the permission to read-write for all the disk.
where /mnt/d you need to change to your mount-point of your disk.

---

### Post by Core407 on 2006-05-31
[QUOTE=bullgr]if the disk is formated in ntfs format then forget it...
ntfs is read-only in linux, some steps are done to support read-write
but it's risky for the moment.

if the disk is not ntfs, then open a terminal and write

to change the permission to read-write for all the disk.
where /mnt/d you need to change to your mount-point of your disk.[/QUOTE]

Well the plan was to tranfer the files I needed to the linux HDD, which i managed to do and then to reformat the ntfs HDD into extend 3 and then transfer the files back onto that HDD.

Edit: Okay, so I reformatted the NTFS HDD into Extend 2, but it's listed as inaccessable. I tried mounting it, but I get;
---------
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
---------
Any ideas?

---

### Post by bullgr on 2006-05-31
you try to mount different file system than you formated the disk...

let's begin from the start...
open a terminal and type
> sudo fdisk /dev/hdb
delete any partition you have in the disk (press d)
after that make a new partition (press a)
select the partition to be 1, and on the other prompts just press enter
after the partition is created, write the partition to disk
and leave fdisk (press w)

now the have to format the partition...
> sudo mkfs.ext2 /dev/hdb1
when the format is ready, make a mount-point
> sudo mkdir /mnt/d
(note that you can give any mount-point you like)

finaly edit the file fstab to auto-mount every time you boot
> sudo gedit /etc/fstab
in the end of file type
>  /dev/hdb1       /mnt/d  ext2        defaults   0       0

optional and last, change the permission to read-write any user
> sudo chmod -R 777 /mnt/d

if you done all this, you will have a new formated disk to ext2 filesystem who's auto-mount every time you boot

hope i help :-D

---

### Post by Core407 on 2006-06-01
[QUOTE=bullgr]you try to mount different file system than you formated the disk...

let's begin from the start...
open a terminal and type

delete any partition you have in the disk (press d)
after that make a new partition (press a)
select the partition to be 1, and on the other prompts just press enter
after the partition is created, write the partition to disk
and leave fdisk (press w)

now the have to format the partition...

when the format is ready, make a mount-point

(note that you can give any mount-point you like)

finaly edit the file fstab to auto-mount every time you boot

in the end of file type


optional and last, change the permission to read-write any user


if you done all this, you will have a new formated disk to ext2 filesystem who's auto-mount every time you boot

hope i help :-D[/QUOTE]

Didn't work. ](*,) 

"d(removed)@d(removed):~$ sudo fdisk /dev/hdb

Command (m for help): d
Partition number (1-8): 1
Warning: partition 1 has empty type

Command (m for help): a
Partition number (1-8): 1
Warning: partition 1 has empty type

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
d(removed)@d(removed):~$ sudo mkfs.ext2 /dev/hdb1
mke2fs 1.38 (30-Jun-2005)
Could not stat /dev/hdb1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?"
---------
That's what I get now. :| The (Removed) part I threw in there so don't mind it. :D

---

