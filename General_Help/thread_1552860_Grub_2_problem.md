---
title: "Grub 2 problem"
date: 2010-08-14
forum: General Help
---

### Post by bob hughes on 2010-08-14
I upgraded to ubuntu 10.04 x64 version from my previous version 9? on my desktop machine.
Doing it late at night I allowed the installation to install grub on all my hard discs(brain confused over discs and partitions)
I have ubuntu on one, windows 7 64Bit on another and windows XP 0n the third. There are no partitions each OS is ona separate disc.
Can anyone advise me of a simple way/utility to remove grub and allow the 2 windows discs to boot independently? I prefer to select which disc to boot from my Bios utility(why do this it allows easier backup)
Any help/guidance gratefully received.

---

### Post by bob hughes on 2010-08-15
(Following up my own post) -- the post "**how to restore the Ubuntu/XP/Vista/7 bootloader (updated for ubuntu 10.04)**" shows how.
However if your version of windows 7 has the infamous KB971033 update which checks for authenticity -mine has- it is now telling me that my 64bit version of windows 7 professional may not be genuine!
I am monitoring to see if this becomes a problem -anybody else had this ?
I didn't use the same windows 7 CD to fix the boot record so I may go back and fix it again with my windows 7 Pro disc.**[B]**[/B]

---

### Post by ahallubuntu on 2010-08-15
FYI, a note on terminology: every hard drive has "partitions" - they may have only one partition, though.  If you have three hard disks in your system, each disk has at least one partition - so you could say you have three partitions total in your system.

Also, Grub doesn't install itself on every hard drive.  During install, it will want to install a boot sector on the MBR of the primary hard drive, though you can choose to install it on a different drive.  So when you installed on your system with three drives, the boot sector was installed on only one of them.  The other two drives should have been completely untouched, unless you were installing Ubuntu on one of them.

My laptop has a tri-boot of XP, Windows 7, and Ubuntu.  For a while I was using the Windows 7 boot loader to boot everything.  The way you do that is to tell Ubuntu during install to install the boot sector not on the primary drive's MBR but to the Ubuntu drive.  So if Windows 7 would have been on sda and Ubuntu would be on sdc, don't have it install the Grub boot sector on sda - tell it to use sdc .  You can do this as an advanced option at the very last step of Ubuntu install before it begins.  

Then, to be able boot Ubuntu from Windows 7, you have to save off that Grub boot sector afterward to a file that Windows 7 can see during boot.  And you also have to muck with the Windows 7 boot loader.  If you want to pursue this, do some googling for info on doing it - I have forgotten the exact instructions, it was some months ago.

---

### Post by Cavsfan on 2010-08-15
Using your original CD/DVD will probably fix this problem.

On a side note since you are dual booting you might want to check out the tutorial in my signature on making the 
GRUB2 menu maintenance free.

I got tired of having to edit my default line every time a kernel was installed and a friend showed me how to do this.
There is even a screenshot at the bottom of it to show you what it can look like.
I just have Ubuntu 64bit and Windows 7 64bit on my PC.

---

### Post by oldfred on 2010-08-15
Is the upgrade still listing all partitions & drives and giving you a choice to overwrite the windows boot loader. I noticed if I run dpkg to reinstall grub, it now only gives drives and Ubuntu partitions. It is a fix they are rolling out.

You can use the windows tools to fix, but window will want to combine boots into one if it sees the other windows. It literally moves the boot files from the second install to the first.

You can install lilo's boot loader to the MBR which works just like windows in that it looks for the active (boot flag) partition and jumps to that to continue booting.

Restore basic windows boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

