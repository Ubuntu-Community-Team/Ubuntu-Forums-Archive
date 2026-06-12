---
title: "Memory Issues on USB Install"
date: 2011-01-09
forum: General Help
---

### Post by bob-linux-user on 2011-01-09
Here is what I did:
I have an external USB Hard Drive 40Gbyte
-Partitioned it 4 ways: approx 17/2/8/10 gig on each partition
-The 17 gig partition was formatted FAT 32
-I rebooted from a Ubuntu 10.10 live CD and used Startup Disk Creator to make a bootable install on the 17 gig partion
-I set aside 4 gigabyte for documents and settings
-Rebooted and it all starts ok
I have have done very little apart from some minor customisations but the computer keeps telling me I have almost no space left.

I rebooted from my usual setup on the internal hard drive to have a look at the files in Nautilus. Nautilus shows there being 17 gig in total and only 821 megabyte used so far. Why is the PC having problems with disk space? by my calcs there should be around 12 gig free (17-(4+1) =14)

Can somebody shed some light please?

---

### Post by PRC09 on 2011-01-09
I dont think you can use the start-up disk creator to install to an regular type USB hard drive or partition.It is for creating a usb version of the live cd....You would have to use the actual live cd or usb bootable version to install where you wish to install.....

---

### Post by C.S.Cameron on 2011-01-09
Have you used Update Manager to do a software update?
That will quickly fill a 4GB casper-rw file.

Edit:
The casper-rw file is where changes are saved.
Once the casper-rw file is full the drive won't boot.

---

### Post by bob-linux-user on 2011-01-10
Thanks PRC09 and C S Cameron

I haven't done a software update. Will not be back on my computer for a few days but will try a full install to the USB key.

Regards

Bob

---

### Post by C.S.Cameron on 2011-01-10
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

### Post by bob-linux-user on 2011-01-15
Thank you C S Cameron!

That worked absolutely brilliantly.

---

