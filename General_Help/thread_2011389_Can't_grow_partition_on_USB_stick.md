---
title: "Can't grow partition on USB stick"
date: 2012-06-27
forum: General Help
---

### Post by TheHitcher on 2012-06-27
Hi all

I'm trying to prepare a usb stick (Toshiba, 32gb) to use as a filesystem device for my Raspberry Pi.

The plan is to write my .img over to it (Which works) then grow the ext4 partition from ~3gb to 32gb and remove the primary partition which is just a boot sector (The pi will boot off a separate sd card)

when I plug it into my Kubuntu laptop and run gparted it can literally take 5-10 minutes for gparted to scan devices and launch (if i remove the usb stick during this it launches straightaway)

Eventually when it opens I tell it to grow the ext4 partition and it just does nothing really. I can leave it for 8 hours and all that will happen is it says it's still doing something but I've a ton of zombie/Disk Sleep processes (Though sdparm just shows a single line with the device name when i give it -a).

I thought it might be a dodgy memory stick (even though it's brand new) but when I plug it into my wife's macbook it recognises it straight away and formats and partitions it to fat32 within a few seconds.

Just hoping that this is a simple newbie question as I haven't done anything with usb drives through linux before, but is there anything that immediately stands outas me having done obviously wrong or is there a usual workaround everyone else knows about?

Cheers!

---

### Post by nipunshakya on 2012-06-27
Try to do your operations by formatting the drive to some other partitions eg. NTFS or ext4,ext3... have u tried that??

---

### Post by TheHitcher on 2012-06-27
Hi, yeah I tried ext3 and it was the same, I've another memory stick on order as well just in case but if I can get this one working then all the better rather than find out I'm back to square one

I didn't try NTFS etc as I wasn't sure whether the pi specifically needed its main partition to be in a certain format, otherwise I could probably just format it as FAT32 on the other laptop and copy across the file system to that, which could be worth a try anyway I suppose..

---

