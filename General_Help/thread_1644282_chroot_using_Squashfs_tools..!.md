---
title: "chroot using Squashfs tools..!"
date: 2010-12-13
forum: General Help
---

### Post by madalasatish on 2010-12-13
I want to customize Ubuntu for distribution in my University..... I followed the commands for Live CD customization...
But an unexpected error occurring...
Please help me out..... 

I installed squashfs tools using command
 **sudo apt-get install squashfs-tools genisoimage**
I am giving my Command lines here,.....

/******* Help me Out to solve this******/
bimber@bimber:~$ mkdir ~/livecdtmp
bimber@bimber:~$ mv ubuntu-10.10-desktop-i386.iso ~/livecdtmp
bimber@bimber:~$ cd ~/livecdtmp
bimber@bimber:~/livecdtmp$ mkdir mnt
bimber@bimber:~/livecdtmp$ sudo mount -o loop ubuntu-10.10-desktop-i386.iso mnt
bimber@bimber:~/livecdtmp$ mkdir extract-cd
bimber@bimber:~/livecdtmp$ rsync --exclude=/casper/filesystem.squashfs -a mnt/ extract-cd
bimber@bimber:~/livecdtmp$ sudo unsquashfs mnt/casper/filesystem.squashfs
Parallel unsquashfs: Using 2 processors
Lseek failed because Invalid argument
read_block: failed to read block @0x7a8bb9d1189c10d6
read_uids_guids: failed to read id table block
FATAL ERROR aborting: failed to uid/gid table
bimber@bimber:~/livecdtmp$

/***********Thank You*******************/

---

### Post by isaacjun16 on 2011-01-09
Same here, did you got any fix 4 that? :confused:

---

