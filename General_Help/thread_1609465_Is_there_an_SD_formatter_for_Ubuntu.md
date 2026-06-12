---
title: "Is there an SD formatter for Ubuntu?"
date: 2010-10-30
forum: General Help
---

### Post by ironic.demise on 2010-10-30
I use a NDS flashcard, mainly for Colors!
I was wondering if there's a format utility for SD cards, and something that does FAT32. because if I format my SD card in Ubuntu the normal way it stops working in my DS until I re-format in Windows.

---

### Post by Boondoklife on 2010-10-30
Ubuntu can format in fat and fat32, just choose the format option and there is a place you can specify what file system to use.

---

### Post by efflandt on 2010-10-30
You could install **gparted** and use that.  I often have to do that if I format the wrong thing (entire disk instead of partition) in Startup Disk Creator.  Although, then I have to first make an msdos partition table, and then the FAT32 partition.  So do not try to format /dev/sdb or /dev/sdf or whatever, you need a number for the partition like /dev/sdb1 or /dev/sdf1.

I never did figure out the default **Disk Utility**.  Once I thought I was using it to change which partition was marked as the boot partition (with grub on a partition instead of mbr) and it started churning endlessly, doing what, I don't know.

---

### Post by ironic.demise on 2010-10-30
But, an SD card has a very slightly different filesystem to that of hard-disks and USB flash drives.

There are Windows utilities (By HP, Panasonic and possibly sandisk) that format an SD card to the filesystem it requires, is THIS possible in 'buntu?

---

### Post by Boondoklife on 2010-10-30
As far as the Utilities you are referring to, if you bought a card that requires a special formating tool to work then I would take it back and get a better one. I have never run into the issues you are running into. SD cards use the same format that any other device uses, this is why a card can be formated on one device, have data placed on it and then put in another device and still be able to read and write from it.

I have a question, you mentioned NDS is that a Nintendo DS? If so then Fat will work just fine.

---

### Post by ironic.demise on 2010-10-30
Yes a Nintendo DS (Lite not I or IXL)
The SD card doesn't *need* a special format, but *every* sd card performs a bit better when formatted using a specified SD formatter, although the filesystem is still the same.

Google SD formatter, it should point out that using an SD formatter software is the *proper* way to format an SD card, Micro or normal.

> How do you normally format your camera SD card? If you use the built-in format option on your camera, that&#8217;s fine, but you shouldn&#8217;t use Windows to format an SD card, at least according to the SD Association. Instead, if you want to prolong the life of your SD card, you should use SD Formatter, a free program that properly formats an SD or SDHC card according to official standards. [http://tinyhacker.com/hacks/format-an-sd-card-properly-using-sdformatter/](http://tinyhacker.com/hacks/format-an-sd-card-properly-using-sdformatter/)

---

