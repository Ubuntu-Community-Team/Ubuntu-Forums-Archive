---
title: "Shared folder between my windows and linux partition"
date: 2011-02-07
forum: General Help
---

### Post by alxpenguin on 2011-02-07
Hi all,

I was wondering if theres a way to create a folder that would be accessible when I boot with windows or ubuntu? Is there some shared location I can place this folder?

Thanks

---

### Post by vat with tux on 2011-02-07
How u have installed ubuntu? means inside windows using wubi installer or as separate OS using bootable cd?

---

### Post by glene77is on 2011-02-07
> **alxpenguin said:**
> Hi all,

I was wondering if theres a way to create a folder that would be accessible when I boot with windows or ubuntu? Is there some shared location I can place this folder?

Thanks

Alx,
I share files by placing them on a USB External HD, and USB FlashDrives. 
Try this with a USB ThumbDrive (flash-drive), and if the applications can normally load the format of your data-file, then they should be able to share.  

Windows will only recognize the NTFS format, not Linux partitions.  
My XP OS will work with the USB External HD. 
Linux will recognize almost any format, on any HD.  
Neat !   Engineer Geeks have written Linux nicely ! 

My main system is XP / Ubuntu,  3 USB External large HD. 
My dev   system is Puppy, Knoppix 6.2, Knoppix 6.4, Puppy 5.1, Watt OS R2, 
all mulit-boot.  
My old system is Win-98, very old, reads only USB 1.0 Ext HD. 
These three computers share this way:
(1) USB manual switch flips 3 USB External HD
(2) USB KVM switcher flips my Keyboard/VideoMonitor
:)   Be glad to share more details.

---

### Post by presence1960 on 2011-02-07
You can make an NTFS partition for shared data. linux can write/read NTFS just fine. I would refrain from writing to the Windows OS partition (C: ) from linux, except in case of emergency troubleshooting/repairs.

---

### Post by glene77is on 2011-02-08
Alx,
Presence is right.  :)
Much simpler.  :)
Basically, just make a new partition with NTFS format. 
Both Windows and Linux can read / share this NTFS partition. 

(since I normally use the USB External HD for storage of everything, 
the data files are already available for 'share' usage)

---

