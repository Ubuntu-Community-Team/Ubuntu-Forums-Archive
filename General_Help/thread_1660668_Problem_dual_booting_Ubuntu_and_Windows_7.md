---
title: "Problem dual booting Ubuntu and Windows 7"
date: 2011-01-05
forum: General Help
---

### Post by ErichFranz on 2011-01-05
I've recently left Windows behind for good and have come to Linux (Ubuntu.)  
However, I've run into problems after trying to dual boot windows 7 and ubuntu.
When I restarted my computer, I got a black screen with white text reading "Minimal BASH-like line editing is supported"

I have the Ubuntu live cd and was able to try Ubuntu without having to install it, but after I put in a flash drive with Windows 7 on it, the Ubuntu CD has stopped working entirely.

The weird thing is, the computer that I installed Ubuntu on, already had Ubuntu and Windows 7 on it.  And every OS was booting successfully.  

The reason I deleted the Ubuntu that was already on the computer, is because there were many different versions.  I wanted to do a clean sweep and only have Ubuntu and Windows 7 installed on the computer.  

PS.  I know that if you try to dual boot Windows 7 and Ubuntu, Windows will overwrite the GRUB file, making it unable to dual boot.  But how can i fix this??  :confused::confused::confused::confused::confused:

---

### Post by oldfred on 2011-01-05
If you know the CD was working before, then it is a BIOS issue on selection of boot device. Once you add USB into the mix it may change the boot order. Have you both changed boot order in BIOS and checked booting with one time boot key (f12 on my system).

I prefer to use USB rather than CD now. It is reuseable and saves the one time use of a CD.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
tps://help.ubuntu.com/community/Installation/FromUSBStick
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by ErichFranz on 2011-01-05
I took out the flash drive and booted it from CD and it still won't work.  

The Ubuntu loading screening will come up and it will load for a long time, but then it will crash and go to a black screen with the text "failed due to unknown user id"

---

### Post by oldfred on 2011-01-06
Sounds like a bad CD or download. Did you check md5sum, link above. Also writing at the slowest speed your CD allows works better also.

---

### Post by ErichFranz on 2011-01-06
I'll check out the link.  

I tried the Ubuntu CD on a different computer and it still didn't work.  
The CD was working fine until recently.  I don't know what happened to it.

---

### Post by ErichFranz on 2011-01-08
I fixed it.  All I did was boot Ubuntu from a flash drive and reinstall the OS.   When I restarted it, everything was working again.  

I went through all this trouble and it was such an easy fix.

---

