---
title: "Grub error"
date: 2009-08-28
forum: General Help
---

### Post by cepacs on 2009-08-28
I used Acronis to move a physical ubuntu box to a VMware VM.  I've done this before and it has worked, but this one is giving me a "Grub Geom Error".  Any ideas on how I can get fix this?

---

### Post by tgeer43 on 2009-08-28
I'm not familiar with the VmWare route but generally speaking this error means:
> This error message will occur if the location of the Stage 2 or Stage 1.5 is not in the area supported by reading the disk with the BIOS directly. This could occur because the BIOS translated geometry has been changed by the user or the disk is moved to another machine or controller after installation, or GRUB was not installed using itself (if it was, the Stage 2 version of this error would have been seen during that process and it would not have completed the install).Most remedies involve changing disk settings in the BIOS. Do a quick Google on "Grub Geom Error" for tips on what to look for and change.

tgeer

---

### Post by cepacs on 2009-08-28
> **tgeer43 said:**
> 
Most remedies involve changing disk settings in the BIOS. Do a quick Google on "Grub Geom Error" for tips on what to look for and change.

tgeer

I did try the disk settings, but didn't have any luck.  I tried a number of things that I found when doing a google search of "Grub Geom Error", but when I couldn't find anything that worked, I came here.

---

