---
title: "Persistent live USB"
date: 2010-12-31
forum: General Help
---

### Post by FalseLobster on 2010-12-31
Hi all!

I'm attempting to create a persistent live USB.

My flash drive is 32 GB, so I plan on creating a 8 or 16 GB ext casper-rw partition for my persistence (as described [here.]("http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/"))

I would like to have the remainder of the space available as an NTFS partition.  However, most of what I'm reading indicates that only FAT32 is possible for a bootable Ubuntu USB.

I've been told that if I simply installed to USB drive as if it were a regular old HDD, it would be bootable and I could simply format the rest as NTFS.  I'm wondering if this is true and why all these utilities I've found (Linux Live USB Creator, Universal USB Installer, etc...) insist on FAT32.

Can anyone advise me what the best way to get what I want... ? I.e. a persistent (>4GB) bootable usb, with the rest of it a windows-recognizable NTFS partition?

---

### Post by C.S.Cameron on 2010-12-31
Windows only sees the first partition on a flash drive.
The NTFS partition must be first.
A 32GB drive is large enough for a Full install:

For a persistent install
The disk image must go on the first partition which must be FAT32. 
A casper-rw partition should be ext2, 3 or 4, not FAT or NTFS.



Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Forward
At "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
Confirm Device is correct.
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 26GB.
Location = Beginning.
"Use as:" = "NTFS file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
(Importent)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are woried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---

