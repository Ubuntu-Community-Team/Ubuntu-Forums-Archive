---
title: "Ubuntu from USB - Booting directly?"
date: 2010-11-30
forum: General Help
---

### Post by misetusame on 2010-11-30
Hi,

as Ubuntu Startup Disk creator is now, it sets up a USB stick. When  booting off USB, after a couple of minutes it asks to "Try" Ubuntu or  "Install".

However, is there a more direct way to "install" Ubuntu directly  to USB, in that it boots directly to that desktop, instead of asking to  try/install each time?

---

### Post by Dans564 on 2010-11-30
I might be wrong, but as of now i think it just loads like the live cd or DVD would.  Not a true install :(  i would like to know how to do that too though. Ubuntu on the computers at my school :p

---

### Post by rummy77 on 2010-11-30
I've previously used flash drive based PDL and DSL distros, which would operate as a linux OS within a windows environment; pretty handy for getting around the protected windows pc's at schools and military bases.  

Like Dans564, I think that the current ubuntu flash drive ISO runs exactly like a DVD or CD, meaning you'll get the same result every time you boot from it.

---

### Post by Dans564 on 2010-11-30
> **rummy77 said:**
> I've previously used flash drive based PDL and DSL distros, which would operate as a linux OS within a windows environment; pretty handy for getting around the protected windows pc's at schools and military bases.  

Like Dans564, I think that the current ubuntu flash drive ISO runs exactly like a DVD or CD, meaning you'll get the same result every time you boot from it.
 

Military bases!!! :?:?:?
Shady shady shady........

---

### Post by rummy77 on 2010-11-30
> **Dans564 said:**
> Military bases!!! :?:?:?
Shady shady shady........

That didn't come out right.  :oops: Sometimes things don't work right on windows, and sometimes your files are in linux formats, and sometimes you just want to use something that works.  But not for any illicit purposes.

---

### Post by Hawkoon on 2010-11-30
You can install Ubuntu to a USB device proper: choose install from the live-stick menu and then on step four, opt for manual partitioning. On the next screen you can select the device on which to install Ubuntu and setup partitions (like swap and root).

Although, I wonder how useful a USB installation is. During the installation the hardware on your system is configured and so on another system your USB installation might not work. A live-stick on the other hand should work on any system.

---

### Post by C.S.Cameron on 2010-11-30
Step by step for installing Ubuntu 10.10 to 16GB portable device.
For other sizes adjust partition sizes to suit:

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

