---
title: "Filename issue backing up CD/DVD to ISO image"
date: 2011-08-28
forum: General Help
---

### Post by jonnan on 2011-08-28
I decided to go ahead and backup a lot of ISO's, game disks, old driver disks et al to my hard drive, basically because I want to be able actually index stuff and not deal with physical disks, and ideally be able to play games without the CD in the drive.

I couldn't get Brasero or K9copy to pull the disk images properly (Brasero doesn't seem to find CD's, and K9Copy insists "Can't open disc /dev/sr0!"), but after some short searches I found K3B which seemed to work, until I did some spot checking.

Some (Not actually all that many) CD/DVD's it backs up fine. But for some reason, many CD's it appends ";1" (sans quotes) to every filename (not folders) and the ISO is then broken. After testing it on a DVD Brasero does the same thing on the same DVD's.

It seems to do it consistently with any given CD/DVD, and I'm finding nothing on this on the Internet (But then try googling for ";1" successfully). Is this a known issue of some kind?

Thanks - Jonnan

Ubuntu 10.04, 64bit

---

### Post by jonnan on 2011-09-13
Does no one else ever backup disks?

---

### Post by emiller12345 on 2011-09-13
Is is possible that you have a bad/incompatible optical drive? Do you have another one handy to swap out and try to see if it has the same effect?  I've had hardware problems in the past that were fixed by making sure that the BIOS has been updated.  Also you should try and make sure that your burning software is the latest and greatest. I've had problems ISO'ing certain CD's in Hardy that were fixed in Lucid, but I still have some that can't be imaged.

---

