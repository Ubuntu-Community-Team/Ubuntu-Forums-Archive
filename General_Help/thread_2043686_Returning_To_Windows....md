---
title: "Returning To Windows..."
date: 2012-08-17
forum: General Help
---

### Post by Shadius on 2012-08-17
Hey everybody! :)

I have a dual-boot setup with Windows and Ubuntu. Windows is on the first hard disk drive and Ubuntu is on the second hard disk drive. What I want to do is get rid of Ubuntu on my second hard disk drive and return my computer to how it was with the single-boot Windows. How do I accomplish this? 

Thanks for the help.

---

### Post by Deepak J on 2012-08-17
You'll have to format the second HDD and install some ver. of windows on the second HDD. It'll rewrite the GRUB with the windows boot loader.

Then just format the second HDD from the existing windows using partition manager...  


Also out of ma curiosity, are you getting rid of Ubuntu...?
If yes, why on earth would you do such a thing....?
(sorry if i'm a bit rude...I'm a great fan of Ubuntu)

---

### Post by Dafydd on 2012-08-17
I think I went back to Windows two or three times around five years ago. Still on Ubuntu though now.

---

### Post by mlentink on 2012-08-17
You might want to read here: [http://ubuntuforums.org/showpost.php?p=12177854&postcount=3](http://ubuntuforums.org/showpost.php?p=12177854&postcount=3)

---

### Post by Shadius on 2012-08-17
> **Deepak J said:**
> You'll have to format the second HDD and install some ver. of windows on the second HDD. It'll rewrite the GRUB with the windows boot loader.

Then just format the second HDD from the existing windows using partition manager...  


Also out of ma curiosity, are you getting rid of Ubuntu...?
If yes, why on earth would you do such a thing....?
(sorry if i'm a bit rude...I'm a great fan of Ubuntu)

Okay, is there another way of getting back the Windows boot loader on my primary HDD because I don't have a Windows installation CD. 

Definitely not getting rid of Ubuntu! I'm a fan of Ubuntu as well. This is just a second old PC that I'd like to put in the living room for others to be able to use who aren't familiar with Ubuntu.

---

### Post by SJR Dorset on 2012-08-17
Install EasyBCD on your Windows installation, its free for non-commercial use. Once installed run it and rewrite the Windows bootloader to the MBR. Restart Windows which should now start without the Grub screen.

When you are in Windows go to Disk Management delete you Ubuntu partition from you second HD and create a new NTFS partition.

---

### Post by Deepak J on 2012-08-17
The below links might help you...

[http://www.sevenforums.com/general-discussion/126020-repair-mbr-without-cd.html](http://www.sevenforums.com/general-discussion/126020-repair-mbr-without-cd.html)

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

