---
title: "Accessing Windows XP [NTFS] &amp; FAT32 Partitions"
date: 2009-08-27
forum: General Help
---

### Post by --ger-- on 2009-08-27
Hi all,
I have a dual boot Windows XP (SP3) and Ubuntu (5.05) laptop ard disk into three partitions, one for Windows, one for Ubuntu a FAT32 pattition for my files. I want to access files stored in both my NTFS Windows Boot partition (my photos) and in the FAT32 partitions while using Ubuntu. From a little bit of research, I believe that this is possible, but I don't know how. I'm a bit of a novice when it comes to Ubuntu and would apreciate it if someone could recommend a step by step idiot's guide to this.
 
Thanks in advance,
Ger

---

### Post by bchurchill on 2009-08-27
Run ```
sudo fdisk -l
``` from a terminal to list your partitions.  The NTFS and VFAT will have device files named something like /dev/sda3 or /dev/hda5 (yours will probably be different).  Then you'll make a directory to "mount" your windows files.  That'll go something like this:

sudo mkdir /windows-ntfs
sudo mkdir /windows-fat

You can, of course, make these folders anywhere and have any name you want (within reason - I don't recommend spaces, although spaces will work.  Just add quotes in the next step.).  Then you run the mount command

sudo mount -t ntfs /dev/___ /windows-ntfs
sudo mount -t vfat /dev/___ /windows-fat

(NOTE: there is a space between the device name and the /windows... folder name)

where the ____ is replaced with the appropriate device.  This attaches the windows file systems to those directories.  Then to see your windows files you can use nautilus or konqueror or use

cd /windows-ntfs

Good luck; let us know if you run into issues.

---

### Post by SuaSwe on 2009-08-27
Here's some tips on doing it using the graphical interface, for those not 100% comfortable with the command line:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by swerdna on 2009-08-27
These will provide the additional detailed steps:
[HowTo Mount NTFS Partitions Read Write in Ubuntu & Kubuntu]("http://ubuntu.swerdna.org/ubuntfs.html")
[HowTo Mount a Fat32 / Vfat Partition Read Write in Ubuntu & Kubuntu]("http://ubuntu.swerdna.org/ubufat32.html")

---

### Post by --ger-- on 2009-08-28
Hi guys,
I just want to say thanks for your help. I finally managed to get it working tonight.
 
Thanks again,
Ger.

---

### Post by SuaSwe on 2009-08-28
Gotta say, I love it when people love Ubuntu!

---

