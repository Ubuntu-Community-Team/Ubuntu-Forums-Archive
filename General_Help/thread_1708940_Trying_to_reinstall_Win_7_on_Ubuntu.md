---
title: "Trying to reinstall Win 7 on Ubuntu"
date: 2011-03-17
forum: General Help
---

### Post by HalfFrozen on 2011-03-17
Hi, I am new here, but have been reading these boards for sometime now.

I have recently switched from Windows 7 on my laptop(about 1 year old now) over to Ubuntu 10.10 and must say it is AMAZING! So fast and smooth. 

Anyways, I am wanting to reinstall Windows 7 again just to have it for some games/programs. And I am running into one small issue, that lot get.

I got a new Windows 7 Ultimate ISO CD(DVD-R) from my tech guy. When I go to launch it from a restart, after making BOOT from the DVD Drive(even made it first to boot in BIOS) it says "Cannot boot from CD error: 5"

I tried it just to see if it would work on my desktop work comp, and it did. But not on my laptop.

The only OS on my laptop is Ubuntu, I had it install along side with windows at first, but I guess I clicked something off. :( 

I really would like to install this WIN 7 Ultimate but just cant ATM..

Any help would be great!
Thanks for your time.

---

### Post by blueridgedog on 2011-03-17
It is your BIOS giving the error, not your current operating system.  Is it a factory disk?  Can your laptop read the disk otherwise (when booted into Ubuntu)?

---

### Post by HalfFrozen on 2011-03-18
> **blueridgedog said:**
> It is your BIOS giving the error, not your current operating system.  Is it a factory disk?  Can your laptop read the disk otherwise (when booted into Ubuntu)?

No, it definitely looks like a burned disk that he gave me...

When Ubuntu is up and going, it does recognize it and its contents.

---

### Post by seawolf167 on 2011-03-18
Before doing anything like updating your BIOS in case that is the issue and your old Mobo cannot recognize the Win 7 boot loader, I'd have your tech guy check the following and reburn a cd/dvd:


[LIST]
[*]is the cd/dvd bootable? (i.e. was it burned as a bootable disc rather than simply a collection of files)
[*]try reburning it at its lowest speed setting, there could be issues with bad/missed sectors
[*]when reburning, make sure to use the "verify" burn setting
[/LIST]

---

### Post by bumder on 2011-03-18
> **HalfFrozen said:**
> 
I got a new Windows 7 Ultimate ISO CD(DVD-R) from my tech guy. When I go to launch it from a restart, after making BOOT from the DVD Drive(even made it first to boot in BIOS) it says "Cannot boot from CD error: 5"

Windows 7 Ultimate **_ISO_** DVD-R?

Does the disc contents just have one .iso file, or loads of folders/files etc?

It may be that the dvd-r has an image of windows 7 on it, in which case, you'll have to mount it to a usb drive or another dvd-r.

Or mayve virtual box...

---

### Post by HalfFrozen on 2011-03-18
> **seawolf167 said:**
> Before doing anything like updating your BIOS in case that is the issue and your old Mobo cannot recognize the Win 7 boot loader, I'd have your tech guy check the following and reburn a cd/dvd:



[LIST]
[*]is the cd/dvd bootable? (i.e. was it burned as a bootable disc rather than simply a collection of files)
[*]try reburning it at its lowest speed setting, there could be issues with bad/missed sectors
[*]when reburning, make sure to use the "verify" burn setting
[/LIST]

Okay, thanks.

> **bumder said:**
> Windows 7 Ultimate **_ISO_** DVD-R?

Does the disc contents just have one .iso file, or loads of folders/files etc?

It may be that the dvd-r has an image of windows 7 on it, in which case, you'll have to mount it to a usb drive or another dvd-r.

Or mayve virtual box...

Contents is just an .iso file.


Also, my desktop has no problem running the same disk from CD/DVD boot mode...

It HAS to be an internal laptop problem...

---

### Post by blueridgedog on 2011-03-18
> **HalfFrozen said:**
> Contents is just an .iso file.

You need to use the ISO file to burn a disk.  The ISO file is an image of a disk and can be burned to disk with the cd/dvd tools that come with Ubuntu.

---

### Post by HalfFrozen on 2011-03-18
> **blueridgedog said:**
> You need to use the ISO file to burn a disk.  The ISO file is an image of a disk and can be burned to disk with the cd/dvd tools that come with Ubuntu.

He got me a new disk just now, and it works!

I told him about the write speed, and it was originally at 8x and he wrote it this time at 1x. 

:D


EDIT: Ran into a new problem, I don't have a NTSF Partition to install Windows to... How do I make a new partition again? GParted?

---

### Post by seawolf167 on 2011-03-18
Windows will format the partition automatically that you select to install on. The only thing you need to do ahead of time is to possibly resize your Ubuntu partitions to make some unallocated space available for Windows to use.

[Here ]("https://help.ubuntu.com/community/WindowsDualBoot")is the official how-to for installing Windows after Ubuntu (scroll down about 1/2 way)

---

