---
title: "mount USB Flash drive"
date: 2010-03-11
forum: General Help
---

### Post by th1bill on 2010-03-11
I'm running 9.10 on a Biostar K8m800M2+ with 2gig of memory, an AMD dual core and today my 64gig flash mounted at boot but the 4gig flash that jhas been there forever did not.  I run lsusb and it is there but I can't get it to remount.  I have changed the port se4veral times but no luck.  In the readout below I see the 4gig stick but not the 64 gig stick although it is mounted and acessable.

th1bill@th1bill-desktop:~$ lsusb
Bus 003 Device 008: ID 0a91:3801 Globlink Technology, Inc. Targus PAKP003 Mouse
Bus 003 Device 007: ID 045e:0734 Microsoft Corp. 
Bus 003 Device 005: ID 0644:0000 TEAC Corp. Floppy
Bus 003 Device 003: ID 058f:9254 Alcor Micro Corp. Hub
Bus 003 Device 002: ID 03eb:3301 Atmel Corp. at43301 4-Port Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 2.0 Stick (4GB) / PNY Attache 4GB Stick
Bus 001 Device 003: ID 04cf:8819 Myson Century, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 1221:3234  
Bus 002 Device 003: ID 0d8c:0121 C-Media Electronics, Inc. 
Bus 002 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
th1bill@th1bill-desktop:~$

---

### Post by michaelqangeles on 2010-03-11
Maybe there's something wrong with your stick? If the 4 gig shows, I don't see why the 64 wouldn't. Make sure your 64 gig stick isn't corrupted to any somewhat.

---

### Post by garvinrick4 on 2010-03-11
Give the flash drive a Label. Say it is flash.

sudo mkdir /media/flash
sudo mount /dev/sdb1 /media/flash
sudo umount /media/flash



1- to make a directory
2- to mount drive.  Get your sdb1 or sdc1 or whatever by running sudo fdisk -l  (a small L) and pick your device #
3- to unmount drive and yes it is umount.

You can label your drive in gparted under System/Admin

---

### Post by th1bill on 2010-03-11
> **garvinrick4 said:**
> Give the flash drive a Label. Say it is flash.

sudo mkdir /media/flash
sudo mount /dev/sdb1 /media/flash
sudo umount /media/flash



1- to make a directory
2- to mount drive.  Get your sdb1 or sdc1 or whatever by running sudo fdisk -l  (a small L) and pick your device #
3- to unmount drive and yes it is umount.

You can label your drive in gparted under System/Admin

Thanks a lot.  When I type "sudo mount /dev/sdj1 media/flash it says that I need to specify the file system type.  I believe I recall it is formatted FAT32

---

### Post by FahadMKS on 2010-03-11
> **garvinrick4 said:**
> Give the flash drive a Label. Say it is flash.
 
sudo mkdir /media/flash
sudo mount /dev/sdb1 /media/flash
sudo umount /media/flash
 
 
 
1- to make a directory
2- to mount drive. Get your sdb1 or sdc1 or whatever by running sudo fdisk -l (a small L) and pick your device #
3- to unmount drive and yes it is umount.
 
You can label your drive in gparted under System/Admin
 
 
You may try the Steps as Root and I am sure that it will work

---

### Post by garvinrick4 on 2010-03-11
> **th1bill said:**
> Thanks a lot.  When I type "sudo mount /dev/sdj1 media/flash it says that I need to specify the file system type.  I believe I recall it is formatted FAT32
Look at that device under drop down menu gparted in gparted to devices pick that device open and see what it is formated in. Do not like the reply specif the file system at all.

---

