---
title: "flash drive not mounting or working?"
date: 2011-01-23
forum: General Help
---

### Post by sdowney717 on 2011-01-23
showing up in lsusb, but nothing in fdisk
it was working, but today it is not working. Same on the XP machine.
so any ideas?

Bus 002 Device 007: ID 058f:1234 [B]Alcor Micro Corp. Flash Drive
[/B]
```
scott@scott-desktop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 055f:021c Mustek Systems, Inc. BearPaw 1200 CU Plus
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 058f:1234 Alcor Micro Corp. Flash Drive
Bus 002 Device 005: ID 045e:00f4 Microsoft Corp. LifeCam VX-6000 (SN9C20x + OV9650)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
scott@scott-desktop:~$ 

```

```
scott@scott-desktop:~$ sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb822ff08

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15260   122575918+   7  HPFS/NTFS
/dev/sda2           15261       90946   607947795    5  Extended
/dev/sda3           90947       91201     2048287+  82  Linux swap / Solaris
/dev/sda5           15261       90946   607947763+  83  Linux
scott@scott-desktop:~$ 

```

---

### Post by dabl on 2011-01-23
They all do die, eventually ...

If the OS (whatever it may be) cannot see the device, then the OS cannot make any changes to it, such as a new partition table or filesystem.  While your USB bus detects a device plugged in, the OS has to see it as a storage type device, for fdisk to address it.

You can plug it into other computers, just to confirm that it's not an issue with your system.  Last stop is the dustbin.  :-({|=

---

### Post by sdowney717 on 2011-01-23
this flash drive when plugged into an xp machine, the machine sees it and gives a drive letter. BUT, it says when clciked, please insert the media.

xp partition manager says media is empty. And the partition manager is no help.

when I first got this a few years ago, it was a fake 16gb ebay drive. 
chinese were selling a lot of fake drives, I got my money back.

I found out after a low level format, it was really only 1.6gb
and since then it has been working ok.

Anyone have a link to the low level formatter ?

found it again
[http://sosfakeflash.wordpress.com/2008/11/01/where-to-download-alcor-tools-to-fix-fake-usb-flash-drives/](http://sosfakeflash.wordpress.com/2008/11/01/where-to-download-alcor-tools-to-fix-fake-usb-flash-drives/)

---

### Post by sdowney717 on 2011-01-27
> Bus 002 Device 008: ID 058f:6387 Alcor Micro Corp. Transcend etFlash Flash Drive

interestingly, I managed to run the LLF format alcormp.exe for this drive with alcor chipset AU6983. After this finished i did not need to do anyother formatting, it was set to fat32

I used pid 6387.
If you notice the pid number changed from 1234 to 6387
first run 'loaddriver.exe' to set pid
then run alcorMP.exe to low level the drive.
once the alcormp.exe file recognizes the flash drive, you get the start menu with the memory block showing up on the page
now it is a 3gb drive again
 
for me it was this file
[http://www.4shared.com/file/69062341/3669b8c1/AlcorMP_080424__AlcorMP_AU698X.html](http://www.4shared.com/file/69062341/3669b8c1/AlcorMP_080424__AlcorMP_AU698X.html)

---

