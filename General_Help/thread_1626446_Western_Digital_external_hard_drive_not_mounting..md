---
title: "Western Digital external hard drive not mounting."
date: 2010-11-20
forum: General Help
---

### Post by VGF on 2010-11-20
I have a 500GB WD external hard drive, that doesn't want to seem to mount in Ubuntu 8.04.  It seems to be one of those deals that recognizes it as a CD in the drive, along with an external hard drive.  When I try to mount the drive, I get an error saying "Unable to mount the volume '*volume name*'".

Not too sure what to do at this point, but I'm sure I'm far from the only one who's had this issue, I've searched around the forums, but it sort of seems like a case-by-case basis for solutions.  Any help?

---

### Post by ajgreeny on 2010-11-20
Let's see the output from ```
sudo fdisk -l
``` in terminal with the WD disk attached, which will show what filesystem the disk is formatted as and may give some clues as to how to mount it.

---

### Post by VGF on 2010-11-20
Okay, entered that into the terminal, and this popped up:
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x58000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdb: 499.4 GB, 499405291520 bytes
255 heads, 63 sectors/track, 60715 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000487a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60716   487699456    7  HPFS/NTFS

```

---

### Post by ajgreeny on 2010-11-20
Ok try this in terminal.
```
sudo mkdir /media/sdb
sudo mount /dev/sdb1 /media/sdb/ -t ntfs -o nls=utf8,umask=0222
```
The first command makes a folder to mount the disk and the second command should mount it to /media/sdb that you just made.

---

### Post by VGF on 2010-11-20
Plugged them in and the second one gives me this:

```
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/sdb -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/sdb ntfs-3g force 0 0
```

I tried the first option and it tells me that only root can do that. The second one simply tells me "permission denied"

---

### Post by ajgreeny on 2010-11-21
You need to use sudo for that No2 command suggested in your quote.

The problem is because the disk was last used on a windows machine, but the "Remove safely" method to unplug it was not followed, and the disk was simply unplugged while still mounted, unfortunately the way most windows users do it.  This means that as far as linux is concerned the disk is still in use as "In use" flags have been added to the file system by windows, but not removed before unplugging.

If you have an option to use a windows machine, simply to plug it in and then remove properly, it is the best way.  If not try the command with sudo, ie ```
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb -o force
```

Sorry for the long post, but it tells you why, as well as how to solve the problem.  Once you have done that, make sure you always unmount it properly in both linux and windows.  It should then mount automatically when plugged in in future, in the way all USB drives do.

---

### Post by muadini on 2010-11-30
Excuse me, I have the same problem though the code's slightly different.  There was a power failure at home and since then, my external harddisk,  Seagate, AgentFree Go, can't be detected. 

Using the code lsusb

this was returned ```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 04f3:02f0 Elan Microelectronics Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 0bc2:2000 Seagate RSS LLC Storage Adapter V3 (TPP)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```Then using sudo fdisk -l

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000482

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13106   105267200    7  HPFS/NTFS
/dev/sda2           13106       30402   138929153    5  Extended
/dev/sda5           13106       25263    97654784   82  Linux swap / Solaris
/dev/sda6           25264       30402    41273344   83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00069a3e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14594   117219328   83  Linux
```I tried this as well: ```
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb -o force
```but this was returned ```
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```I won't mind formatting my Go, but I want to recover most "memories" from it first, so I'm open to solutions. 
Thank you!!!

---

### Post by endotherm on 2010-11-30
muadini, your best bet is to plug the drive into a windows system and perform a chkdsk scan and repair on it. it's best to use the MS tools for NTFS when at all possible. 

VFG, your best bet is to do the same, plug into a windows box, and reboot. unplug your drive before the system is booting back up. then try again. if you believe your drive is healthy, and no IO operations were occurring at the time of the disconnect, then just use the mount command with both sudo and the force option.

---

### Post by muadini on 2010-11-30
Dear endotherm, 

Thank you for your help :) I tried doing that via run in my dad's vista, but it just closed after finishing scanning. 

I managed to download a free date recovery software(stated that it only works for Seagate and Maxtor) from [www.salvagedata.com](www.salvagedata.com) and also seatools from Seagate's webby.

Right now, I am trying to recover the hdd using the program, hopefully after the elasped hr or so, I have gd news :D

---

### Post by muadini on 2010-11-30
The data can be recovered with Salvagedata Recovery, but I have to buy it :cry: 

Currently searching for free data recovery programs, any recommendations anyone?

I want to try all options before using the advanced tools in seatools as it might wipe the data.

---

### Post by sepo on 2010-11-30
Hi had a similar problem this weekend with every usb disk....let's try this (taken from my other post 'Cannot detect USB disks on eeepc'):

Opening System -> Administration -> Disk Utility I saw that the system has detected the usbpen (/dev/sdb1) as mounted on / .

In my case the system wasn't able to mount because the usb disk (sdb1) seemed already mounted as the main disk. You can try to see what Disk Utility tells you about the disk.
One quick test to verify if you have my same problem is to attach any usb disk or pen and THEN attach your western digital....in this case the 1st comes as sdb1 and the latter as sdb2 (that probably it's unmounted and free :) )

---

