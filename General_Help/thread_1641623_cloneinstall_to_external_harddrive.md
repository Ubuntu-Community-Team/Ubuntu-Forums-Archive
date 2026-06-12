---
title: "clone/install to external harddrive"
date: 2010-12-09
forum: General Help
---

### Post by dirty_harry on 2010-12-09
I have a working 10.04 installation on my notebook. 
I would like to play around and install stuff but not on my productive system. I tried simply to make another installation via text mode on my external drive... well, it worked till the grub installation failed.

I was googling around and found that I probably want an USB-Pendrive with persistent mode:
[https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks](https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks)
But can I install drivers or software and so on this? Isn't it "a OS to carry files around"?

It does not have to be portable! No need for a Live-system that works on every machine! 
I was also looking for a way to clone my running system to the usb-drive. But I have several partions and added (with the freespace) together it's bigger as my external drive(available 40GB and 200GB, the 40 one would be nice) - come to think of it, it is an extended part:
```
:~$ sudo fdisk -l /dev/sda

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1               1        1275    10241406   1c  Verst. W95 FAT32 (LBA)
/dev/sda2   *        1276       11513    82236124+   7  HPFS/NTFS
/dev/sda3           11514       11774     2096482+  82  Linux Swap / Solaris
[B]/dev/sda4           11775       38913   217993987    5  Erweiterte
/dev/sda5   *       11775       19069    58597056   83  Linux
/dev/sda6           19070       38913   159396898+  83  Linux[/B]

```Maybe clonezilla?

thx, harry

---

### Post by Rubi1200 on 2010-12-09
Clonezilla is definitely an option worth considering:
[http://clonezilla.org/](http://clonezilla.org/)

An Ubuntu install with persistence means you can install software, save files, and change settings all of which will be saved for the next time you use the USB stick:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by C.S.Cameron on 2010-12-10
You can do a Full install to USB pen drive similar to internal HDD.
It will operate just the same, load drivers, updates, upgrades, install software, etc.

Step by step for 10.10:

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

### Post by dirty_harry on 2010-12-15
thx for the replies

but right now I'm having serious hardware trouble with my laptop, looks like too much dust is in there and I can't find the screwdriver to...[COLOR=#000000][FONT=Arial][FONT=Tahoma]
[/FONT][/FONT][/COLOR]
and my desktop is more or less disassembled.

you see, I busy holding everything together.

anyway, thx
[COLOR=#000000][FONT=Arial][FONT=Tahoma]
[/FONT][/FONT][/COLOR]

---

