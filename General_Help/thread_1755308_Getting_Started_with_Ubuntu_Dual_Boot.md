---
title: "Getting Started with Ubuntu Dual Boot"
date: 2011-05-11
forum: General Help
---

### Post by Mr. Monkey on 2011-05-11
I have never touched Linux.  Always been intrigued, but never toyed around with it until now. So please bear with me. :)

I normally run Windows 7 Pro but would like to dual boot Ubuntu.  I have installed Ubuntu 11.4 with Wubi 4-5 times, and it starts out fine, and then stops working on me.  I tried recreating it to see what was causing the problem, but with no avail.  The problem it has is as soon as I pick Ubuntu from the GRUB it boots to some sort of bootup (non GUI) and gets to a point where it says something about a system audit, and never loads from there.  The only way to fix it is to uninstall Ubuntu (through Add/Remove Programs) and reinstall. 

I am not in a place where I can partition drives or anything like that.  I do not care so much about using Wubi, but either that, or help booting from a USB would work fine for my needs.  Unfortunately most of the links in the beginners guide / FAQs are dead and didn't lead me anywhere.

My specs are:
Windows 7 Pro x64
ATI Mobility HD 5470 Graphics
8 GB RAM
ASUS B53F laptop

I'm not sure what other info you might need.  But any help is greatly appreciated.  I'd hate to give up on Linux this fast.

---

### Post by dragonfly41 on 2011-05-11
I've gone through the apprenticeship of mixing Windows Vista and XP with ubuntu and soon dropped the use of wubi ("install alongside windows"). Now I have ubuntu in a separate partition with Windows Vista in other partitions.   Gradually migrating.

I also have another bootable ubuntu in a separate USB drive (which is what you want).

The steps I would take:

(1) download unetbootin (there is a windows version and a linux version)

    [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
    [http://wiki.geteasypeasy.com/How_to:_Using_Unetbootin](http://wiki.geteasypeasy.com/How_to:_Using_Unetbootin)

(2) if you have ubuntu LiveCD use gparted to create four logical partitions in an extended partition in your USB drive

    logical partition 1     for ubuntu "/" mount          format ext4      bootable flag set=true
    logical partition 2     for ubuntu "/home" mount      format ext4
    logical partition 3     for ubuntu "swap" (optional)       format swap
    logical partition 4     for sharing data between windows and ubuntu        format ntfs

(3) using unetbootin .. probably from your windows OS .. burn ubuntu iso into logical partitions 1, 2 and 3) .. note: "swap" partition is optional and separating "/" and "/home" mounts is discussed eleswhere in the forum.   ntfs partition is also optional .. but useful so that you can view common files (windows can't view ext format but linux can view ntfs format)

(4) in bios boot from USB device (might be F12 to select bootable device).


[EDIT] Just noted that you have 8 GB RAM so probably you will not benefit much from having a separate "swap" partition.

Also read here ..

[http://www.linlap.com/wiki/asus+b53f](http://www.linlap.com/wiki/asus+b53f)

---

