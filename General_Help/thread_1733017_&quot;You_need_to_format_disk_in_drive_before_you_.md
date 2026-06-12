---
title: "&quot;You need to format disk in drive before you can use it.&quot; error"
date: 2011-04-18
forum: General Help
---

### Post by sabatron on 2011-04-18
So I have a patriot xporter 4gb flash drive. I actually have 2 of them. Both worked great until one of them all of a sudden gives me that error when I plug it in. I click format and windows says that it can't format it. i go to properties and it says the capacity is unknown and that its FAT not FAT32 like the other one is. so i try the quick format in all of the other types (ntfs and xfat) and I can't format it that way either...FAT32 is not even an option even though that's the default for the other one. It seems as if the flashdrive got corrupted. I tried it in 2 other pc's (one with vista and one with ubuntu gutsy) and I still get the same issue. the drive just can not work. I'm running out of ideas here.... i tried the chckdsk e: /f command in command prompt as well and it says that the file system is RAW and that chkdsk is not available for RAW drives. Any advice on how to get this flash drive working again? It doesn't have anything important on it so I'm totally down with formatting it but windows won't let me! should i try gparted or something? This happened right after i plugged it into my new laptop that had win 7 64 bit on it and now it stopped working in any pc with any OS. is the drive completely useless now?

---

### Post by 3Miro on 2011-04-18
If you don't have anything important on it, you can try gparted (seems like you know what it is and possibly how to use it).

I had a motherboard once kill 2 flash drives. I may have connected it wrongly (as it was desktop motherboard), but it did kill the flash drives. You can try the flash port of your laptop with something like a phone, my phone will either charge from a USB port or use it to connect as a storage device. The USB drives would die as the motherboard gave them power as if to charge a device, instead of data signal. The phone can handle either, so it should be safe to test the ports.

---

### Post by dcstar on 2011-04-20
> **sabatron said:**
> 
........
is the drive completely useless now?

[LIST=1]
[*]Possibly.
[*]Use gparted to put a new Partition Table on the device.
[*]Upgrade from an obsolete Ubuntu version (7.10).
[/LIST]

---

