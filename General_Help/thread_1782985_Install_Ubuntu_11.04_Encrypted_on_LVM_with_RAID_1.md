---
title: "Install Ubuntu 11.04 Encrypted on LVM with RAID 1"
date: 2011-06-15
forum: General Help
---

### Post by Kissell on 2011-06-15
I want to do a fresh install of Ubuntu.  Until now I have always just installed to a single drive, never used RAID for my root file system, or encrypted it, or used LVM.  Frankly, I don't see the point of LVM, I normally just dedicate an old 250GB disk to the root file system and leave all the partition defaults, and run my data encrypted on a large multidisk raid array.  I don't see the point of LVM, because so what if you can change partition sizes, you should never need to, there is no way ubuntu is ever going to fill up all that space, even if you install all the apps in the store, but, it is raved about, so I thought I would give LVM a try.  While I am reformatting, I wanted to encrypt everything as much as possible, except the small 100mb boot partition, and I have an extra 250gb disk, so I thought I might as well software mirror the OS disk.  Normally I just dedicate a disk to the OS and keep my data separate, if I need to reinstall the OS, no big deal, it doesn't take that long, and I don't care about /home, there's nothing in there important, all the real data is on the multidisk array where I keep my data, safe from my reformats of the drive that has the OS on it...  but, I would like to encrypt the OS drive, and I would like it running RAID 1 so that I don't have to fix it "right now" if a disk breaks...  I can choose to put the fire out at a more convinient time like on saturday.  So while I am doing encryption and mirroring, I might as well setup LVM...

Does anyone have any links to walkthroughs on how to do this?  I can't find any, only separate walkthroughs, but not all of them together.

Also, if I can mirror on raid 1 and install the OS on that...  then theoretically, I don't see any reason I couldn't install Ubuntu on my ten disk raid-6, and not use the 250gb OS disks at all.  Although it is nice having the data physically separate, so that no mistakes are make reinstalling the OS in the future and formatting the wrong partition.

---

