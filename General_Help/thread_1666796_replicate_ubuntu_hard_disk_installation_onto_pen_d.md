---
title: "replicate ubuntu hard disk installation onto pen drive"
date: 2011-01-14
forum: General Help
---

### Post by kanishkdudeja on 2011-01-14
i hav ubuntu installed onto my hard disk..

now i want the same installation with all the packages to be replicated on a pen drive..

so that i can use ubuntu on other pcs with a bootable pen drive with all my packages installed.

i dont want to create an installation usb..

jus a usb which contains my full hard drive installation and can run on any system which supports bootable usb..

my filesystem size is 5.5gb and pen drive size is 8gb.

---

### Post by C.S.Cameron on 2011-01-14
You can use remastersys to make a backup iso of your hard disk install.
You can use this with Startup Disk Creator to install to pendrive or the iso to install to CD.
You can use the Live CD or pendrive to do a full install to another pendrive or to hard disk.

or you can shrink your hard drive partition to less than 8GB and use dd to clone it to flash drive:

```
sudo dd if=/dev/sda of=/dev/sdb
```

where sda is the drive you wish to clone and sdb is the target drive.

Following is a step by step to Full install 10.10 to flash drive:


Following step by step for Full install of 10.10 to USB device, adjust partition size to suit:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD or Live USB.
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

### Post by C.S.Cameron on 2011-01-14
You can use remastersys to make a backup iso of your hard disk install.
You can use this with Startup Disk Creator to install to pendrive or the iso to install to CD.
You can use the Live CD or pendrive to do a full install to another pendrive or to hard disk.

or you can shrink your hard drive partition to less than 8GB and use dd to clone it to flash drive:

```
sudo dd if=/dev/sda of=/dev/sdb
```

where sda is the drive you wish to clone and sdb is the target drive.

Following is a step by step to Full install 10.10 to flash drive:


Following step by step for Full install of 10.10 to USB device, adjust partition size to suit:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD or Live USB.
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

### Post by kanishkdudeja on 2011-01-15
if i clone my hard disk to usb..still my usb wont be bootable..would it ?

---

### Post by C.S.Cameron on 2011-01-15
> **kanishkdudeja said:**
> if i clone my hard disk to usb..still my usb wont be bootable..would it ?

If you clone the whole drive with dd it will be.

---

### Post by kanishkdudeja on 2011-01-15
okay..thanks..:)

---

