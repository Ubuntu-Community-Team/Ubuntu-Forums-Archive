---
title: "Full install on USB flash drive or External HDD"
date: 2011-01-14
forum: General Help
---

### Post by Andy06 on 2011-01-14
So I'm planning to do a full install on a flash drive. I searched the forums for previous threads and there were loads. Was there a BIG one that I missed in the mess? If so, please direct me to it.

There was two contentious issues in all the threads and I'd like em resolved once and for all :D

1.Should I or should I not make a swap partition on the flash drive? What about /var, /tmp and /log?

2.Also can someone rank the following in terms of access speed and snappiness:

1) Live CD
2) Live USB with or without persistence (average Sandisk stick)
3) External 2.5" HDD (5400-7200 RPM connected via USB 2.0)
4) Internal 5400-7200RPM HDD using SATAII
5) Full install on USB flash stick (average Sandisk stick)

Thanks

---

### Post by C.S.Cameron on 2011-01-14
I think if you put enough swap on a flash drive you can hibernate. 
Probably not a good idea on 4GB drives, might be useful if drive has lots of space.

1) Internal 5400-7200RPM HDD using SATAII
2) External 2.5" HDD (5400-7200 RPM connected via USB 2.0)
3) Full install on USB flash stick (average Sandisk stick)
3) Live USB with or without persistence (average Sandisk stick)
4) Live CD

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

### Post by Andy06 on 2011-01-15
Thanks for the detailed instructions :D

Won't be doing on a desktop though. It's for a uni thing where we used to hand out flash drives to people walking by, those were LiveUSBs, now we're gonna do full installs instead.

Just two questions:

1. Is swap such a good idea? It might wear out one particular area of the drive. Hibernation is not needed and most computers sold nowadays have at least 3-4GB of RAM. Ubuntu doesn't even use 10-15% of that on idle so swap is rarely ever used or accessed.

2. Are external HDD installs always faster than flash drive installs? In my experience, its a bit random in that the flash drives load apps faster (lower seek times and latency) but for large apps and transfers and write operations, the external HDD does better once its up and spinning away. That's why I asked since I was a bit confused by that.

---

### Post by Copperblade on 2011-01-15
> **Andy06 said:**
> 
1.Should I or should I not make a swap partition on the flash drive? What about /var, /tmp and /log?


If I had enough memory I wouldn't use a swap on flash.  I think you're going to need /var and /tmp for your system, whether they're separate partitions is at least somewhat orthogonal to the question of external media.  Just remember to use noatime or at least relatime options.

---

### Post by C.S.Cameron on 2011-01-15
The step by step is for flash drive or other USB drive.

I don't use swap on flash drives myself but do use it in USB HDD's.

You are probably right about speed, I'm just going by published speeds.

---

### Post by cL0h on 2011-06-13
> **C.S.Cameron said:**
> 

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
Select "Primary", "New partition size ..." = 3 to 4 GB, 


Hi there C.S. Cameron. Please excuse my total ignorance but why do you recommend creating a 1 GB FAT partition?

I am trying to create a Linux system that boots from an OCZ Rally2 4GB USB key. I won't have any other OS installed.

Is there a reason to create the FAT partition. Is it for booting? Is anything installed on it?

---

### Post by oldfred on 2011-06-13
@ cL0h
Welcome to the forums.

The FAT partition is so you can use it with Windows. Windows only reads FAT or NTFS and only the first partition. So it is just for data to allow transfer from windows if you want.

If only a 4GB flash drive you cannot use 11.04 as it wants 4.4 to install. Older versions will install to a 4GB flash but it is tight. You have to regularly houseclean and maybe down grade from some of the largest apps like Firefox to Chromium browser. And uninstall OpenOffice and use Gnumeric and AbiWord. You will not have room for swap or the FAT partition if only 4GB flash.

---

### Post by C.S.Cameron on 2011-06-13
> **cL0h said:**
> Hi there C.S. Cameron. Please excuse my total ignorance but why do you recommend creating a 1 GB FAT partition?

I am trying to create a Linux system that boots from an OCZ Rally2 4GB USB key. I won't have any other OS installed.

Is there a reason to create the FAT partition. Is it for booting? Is anything installed on it?

As OldFred mentioned it is so you can plug your drive into a Windows computer and copy data to/from it.

If you only use Linux or plan to use this flash drive as a fixed drive this option should be ignored.

A 4GB flash drive is not large enough for 11.04, it requires minimum 4.4GB.
10.04 LTS will work on a 4GB stick.

---

