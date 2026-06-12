---
title: "Dell Studio 15 Problem"
date: 2009-10-16
forum: General Help
---

### Post by Vishnu V on 2009-10-16
Hi

I installed ubuntu in my new dell studio 15 and i found some problems with it.
I found that the multimedia keys (eject,WLAN, brightness control) are working only for the first minute after the booting
the second problem is after making desktop effects to extra or normal  ubuntu freezes when tried to i maximize or minimize videos 
I have  ATI 4570 (512 MB) Graphics card

please Help

Thanks in advance

---

### Post by nexes128 on 2009-10-16
Can you tell me if you have a bluetooth keyboard and mouse as ubuntu, can have issues with theses?
If they are check this out [http://ubuntuforums.org/showthread.php?t=227057](http://ubuntuforums.org/showthread.php?t=227057).

For the second part did you install the ATI drivers, also are you tring to play flash videos(like you tube) the flash player for linux also has some know issues with that.

---

### Post by Vishnu V on 2009-10-17
I dont have a bluetooth mouse or keyboard

---

### Post by clevertomato on 2010-01-26
I have a Studio 1555 with ATI 4570. I'm running Karmic amd64 on mine with no problems. 

What works for me and what I stuck with is:

1. Installed Karmic from CD as you normally would.
2. Installed proprietary ATI drivers via System/Administration/Hardware Drivers (OR via terminal with "sudo apt-get install xorg-driver-fglrx fglrx-amdcccle")
3. Added " noapic" to the end of the appropriate line in my Grub file to get the brightness Fn keys working and the lid closure behavior working (note I did NOT have to change any ACPI settings)

I hope this helps.

---

