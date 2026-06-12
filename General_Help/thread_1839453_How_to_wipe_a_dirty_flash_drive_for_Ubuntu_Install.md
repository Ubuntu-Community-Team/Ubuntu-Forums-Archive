---
title: "How to wipe a dirty flash drive for Ubuntu Installation"
date: 2011-09-05
forum: General Help
---

### Post by rende on 2011-09-05
Hi,

I was recently at a conference sponsored by Intel (among others) and they were giving away free 4gb flash drives.  I picked one up only to find it contains some malware and is formatted very strange.

When I put it in a Windows machine, the virus detection instantly picks up a trojan called xcrypt.gen2.  The other strange thing is it creates a new drive that appears as a CD-ROM device.

Now when I plug it into my Ubuntu box, the virus is not a concern, but it still mounts another drive called CD_ under /mount as well as the main partition on the flash drive which includes a bunch of pdfs from Intel.


What I want to do is use the flash drive as an Ubuntu installer for a netbook.  I tried using the "Startup Disk Creator" under System->Administartion to erase the drive but it freezes and fails to respond and I must force quit.  I imagine this is due to the strange behavior/formatting of the flash drive.  

I also tried running sudo mkfs.ext3 /dev/sdb1 on the drive, this is the partition that shows up in fdisk -l.   But after running this command fdisk still shows a bootable FAT32 partition and startup disk creator is still crashing.  Here's what I see when I run fdisk -l:

Disk /dev/sdb: 4043 MB, 4043980800 bytes
125 heads, 62 sectors/track, 1019 cylinders
Units = cylinders of 7750 * 512 = 3968000 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b47e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1019     3948594    c  W95 FAT32 (LBA)

This is after I ran mkfs.ext3 /dev/sdb1 

And it still mounting something under /mount/CD_ whenever I plug it in, as well as the USB drive showing up as 4gb usb drive in the file browser.

---

### Post by ajgreeny on 2011-09-05
It sounds as if the safest way is to use gparted, either from your installed OS, if you have it in your system, or beter using a live CD, and go to **Device->Create new partition table** in the menus.  That should remove anything that was on the drive and allow you to make a new partition or partitions to use as you wish.

Just make sure you get the right device or you're in big trouble;  you could wipe everything from your hard drive.

---

### Post by linuxuser12345 on 2011-09-05
Just right click on it and find "Format." That works for me, and hopefully your answer is this simple too.

---

### Post by yetiman64 on 2011-09-05
Personally OP with something like you describe that registers as a new cd drive etc, I would suspect has some interesting bootcode running. 

In this case a simple format may not be enough. AJGreeny's suggestion with gparted will definitely do the trick, but pay particular attention to the warning that was given, mis-identify the drive and you can loose your whole install. Take care.

---

