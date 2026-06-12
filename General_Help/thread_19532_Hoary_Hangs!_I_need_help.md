---
title: "Hoary Hangs! I need help"
date: 2005-03-12
forum: General Help
---

### Post by iroko on 2005-03-12
I'm new to Linux and Ubuntu. I recently tried the Warty LiveCD which worked just fine on my machine. It detected all my peripherals and setup and booted without a problem.

However when I boot with the 5.04 Preview LiveCds (both AMD64 and 32bit) it doesn't automatically detect my settings (keyboard layout for instance) and it hangs when it gets to the splash screen. I've burn't a number of CDs sourced from the mirror servers and via Bittorrent but it doesn't make any difference.

My set up is
AMD Athlon 64 3200+ (939 pin)
ASUS A8N-SLI MOTHERBOARD (nvidia NfORCE4 SLI chipset)
512 MB PC3200 DDR RAM
Seagate 200GB SATA hard disk
Onboard sound
128MB ATI Radeon X600Pro Graphics card

Any help would be appreciated.

---

### Post by steffen on 2005-03-12
There are some problems with 64 bit Ubuntu. [http://www.ubuntuforums.org/showthread.php?t=17424](http://www.ubuntuforums.org/showthread.php?t=17424)

---

### Post by iroko on 2005-03-12
[QUOTE=steffen]There are some problems with 64 bit Ubuntu. [http://www.ubuntuforums.org/showthread.php?t=17424](http://www.ubuntuforums.org/showthread.php?t=17424)[/QUOTE]

Thanks for your reply but it doesn't explain why the 32 bit LiveCD doesn't work any more (as it did with the Warty LiveCD).

Dows anybody have any ideas how I can find the source of the problem?

---

### Post by steffen on 2005-03-12
How does it hang? Any symptoms or errors?

---

### Post by iroko on 2005-03-12
[QUOTE=steffen]How does it hang? Any symptoms or errors?[/QUOTE]

The boot sequence appears to be OK, (I'm asked to identify the language, keyboard type and screen resoultuion), the splash screen is displayed and then the screen and the (cordless Logitech) mouse just freeze. There are no obvious error messages that I can identify.

---

### Post by steffen on 2005-03-16
Hi iroko,

I don't have the technical expertise myself, but if you post your /var/log/Xorg.0.log and
/etc/X11/xorg.conf files, someone might be able to assist you...

---

