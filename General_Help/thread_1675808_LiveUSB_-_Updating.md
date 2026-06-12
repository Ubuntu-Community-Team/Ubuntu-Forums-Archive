---
title: "LiveUSB - Updating"
date: 2011-01-26
forum: General Help
---

### Post by Tony_L on 2011-01-26
Is there any way to update a LiveUSB and have it stay updated? yet still 'live'

IE, create usb from 10.10.
Boot off USB, - update,
reboot, updates still applied?

---

### Post by khamil8686 on 2011-01-26
do you mean boot from a memory stick and then update your live session's files using synaptic and then you reboot and boot from usb again into a new live session and your live session will have all the updated files? im not totally clear on your question

---

### Post by Tony_L on 2011-01-26
yes

---

### Post by khamil8686 on 2011-01-26
the live usb or cd loads itself into ram i believe and then once you reboot it clears data from ram so the only way to update the files on the live usb would be to download the specific .deb files you want updated manually and then copy them over to the live usb where you could run them in your live session

heres a link to create a live cd from scratch :)
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

heres where to download .deb files from the repos manually
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by C.S.Cameron on 2011-01-26
If you try updating or upgrading a Live USB, the casper-rw file where changes are saved will quickly fill and the drive will no longer be bootable. The kernel is part of a squashfile and can't be modified.
If you want a updateable flash drive you must  do a full install.

Following step by step for Full install of 10.10 to USB device, adjust partition size to suit:

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
Make "New partition size..." about 1GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
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

