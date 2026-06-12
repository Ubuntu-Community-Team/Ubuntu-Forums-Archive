---
title: "Ubuntu 10.10 bootable flash key problem"
date: 2010-12-23
forum: General Help
---

### Post by darkworld on 2010-12-23
I have made a usb ubuntu bootable memory stick following ubuntu instructions, using startup disk creator, i used a fresh burnt cd with correct md5 checksum, 32 bit desktop 386i created the key with 4 gb persistence area, the key is 8Gb corsair. 

I have made keys before successfully. Ive tried several attempts and I even tried using iso image in windows with the software to create the key as per ubuntu instructions. Every time the key makes successfully. Then this happens

I put usb key in pc, boot, it starts to boot ubuntu, it gets as far as ubuntu logo with 5 dots scanning across and stays at this point.

I just hit F1 and got this message.

> (process:411) Glib - Warning ** : getpwuid_r(): failed due to unknown user id (0)     Stdin:error 0 

Im not an expert but that looks like something to do with passwords???...any help much appreciated...it a crimbo present for a friend.

---

### Post by darkworld on 2010-12-23
is there a better forum to place this question in?

---

### Post by C.S.Cameron on 2010-12-23
Does your computer have at least 500MB RAM?

8GB flash drive is large enough for a Full install:

Following is a step by step:

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
(Optional partition for use on Windows machine)
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 4GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 to 6 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 to 8 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap space, allows hybernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB, same size as RAM), Beginning and "Use as" = "swap area" then OK.
(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---

### Post by dcstar on 2010-12-24
> **darkworld said:**
> I have made a usb ubuntu bootable memory stick following ubuntu instructions, using startup disk creator, i used a fresh burnt cd with correct md5 checksum, 32 bit desktop 386i created the key with** 4 gb **persistence area, the key is 8Gb corsair. 
.........

Personally I would not use a Persistence size so close to the FAT32 limit. Try it with just 2GB and see what happens.

---

