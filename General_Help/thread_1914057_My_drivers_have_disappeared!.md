---
title: "My drivers have disappeared!"
date: 2012-01-23
forum: General Help
---

### Post by 0011235813 on 2012-01-23
I have just updated Ubuntu. For some reason, after the updates completed, my computer wouldn't respond. I shut it down. But now, when I booted into Ubuntu- surprise! My proprietary drivers have gone bye-bye, and I cannot connect to the internet with my Wi-Fi card! Furthermore, the driver for my graphics is gone too, so it's Unity 2d fallback for me. 
I am now forced to use the Windows XP (thank goodness for dual-boot) which has working Wi-Fi.

I am now thinking how to solve this issue- attempt to connect via ethernet and hopefully download the drivers from USC? Or do a fresh install?

I don't think I'm going to do another update ever again.

---

### Post by gandaran on 2012-01-23
how did you install drivers or what packges did you use?
always try installing drivers from packages provided in the software center, compiling or installing some driver packages from other sources you may have to re-install every time there is a kernel update.

---

### Post by 0011235813 on 2012-01-23
> **gandaran said:**
> how did you install drivers or what packges did you use?
always try installing drivers from packages provided in the software center, compiling or installing some driver packages from other sources you may have to re-install every time there is a kernel update.

I did not self-compile anything. The drivers came along with my Ubuntu installation. I have tried to download a package from USC- apparently, my packet system is broken! It says to disable all third party repository's, how do I do this?

---

### Post by 0011235813 on 2012-01-24
I've fixed the package issues with:
```
sudo apt-get -f install
```
However, I have not found propietary drivers that are missing (Wi-Fi, graphics,mousepad). Apparentely, theyare already installed. I'm thinking of trying to re-install them. If that doesn't work, I'll have to backup my files to one of my external disks, if I can't do that- I'll see if it can fit on my Windows partition. I'll then have to do a fresh install with either wubi or CD (that's assuming the optical drive still works).
 
Unless somebody happens to know a way to "factory reset" Ubuntu without re-installation?

---

### Post by 0011235813 on 2012-01-24
Problem Fixed!!
I booted into recovery mode and my drivers are back! Graphics are working, mousepad is working.... And the Wi-Fi is working!
For any of you guys out there who experience this; use:
```
sudo apt-get -f install
```
To fix apt problems, and boot into recovery mode to fix it! 
Important Note: After a while, it will no longer do anything, it will say something like "mounted SCSI disk". That's when you know it's fixed it, and then you boot properly.

---

