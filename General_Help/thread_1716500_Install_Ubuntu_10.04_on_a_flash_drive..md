---
title: "Install Ubuntu 10.04 on a flash drive."
date: 2011-03-28
forum: General Help
---

### Post by stchman on 2011-03-28
Hello all.

I am wanting to build a NAS.  There are lots of pre-built NAS boxes out there, but what fun would that be?

I have many 8GB USB drives and would want to install Lucid on the drive.  I don't mean create a bootable USB flash drive in place of the LiveCD, I mean install the OS to a USB drive and boot the computer using the flash drive.  This way the OS would have 8GB of space and could access say a 1TB HDD added to the PC.

Once I get the OS installed on the USB drive I would install NFS and Samba.  I could then remote into the NAS and make changes if needed.

From everything I have read, I would need to not have a swap file on the USB drive as well.

Any thoughts would be appreciated.

---

### Post by C.S.Cameron on 2011-03-28
Following a step by step for installing 8.04 on a 8GB flash drive.
You probably don't need anything but the / partition.
This will be a little slower than using a SATA drive.

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu 10.04.
Fill in "Time Zone" and "Keyboard layout".
At "Prepare disk space" select "Specify partitions manually (advanced)".
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
Click "Forward".
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Select forward.
Select Install.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you select the "Advanced" button and choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your hard drive, even when booting another computer.

---

