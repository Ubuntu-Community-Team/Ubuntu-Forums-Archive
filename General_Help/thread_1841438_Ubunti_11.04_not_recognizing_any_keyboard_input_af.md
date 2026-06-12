---
title: "Ubunti 11.04 not recognizing any keyboard input after boot"
date: 2011-09-09
forum: General Help
---

### Post by srobtjones on 2011-09-09
My hardware is an HP a6700f desktop, 7GB RAM, Intel X-25 SSD hdd. MY OS is Ubuntu 11.04 64-bit (my processor is Intel 64-bit).

Every day I make it search for new updates. When it finds any I let them install.

I did so two nights ago before going to bed. Everything worked after the install. Everything seemed normal.

When I got home from work yesterday evening I booted the machine normally. When the login screen came up, the keyboard would not work. I tried two different keyboards, both USB & PS2, but neither of them worked.

When booting, the keyboards are seen by the BIOS because I can press the F keys to get into BIOS, Boot options, etc. Ubuntu won't recognize the keyboard once I get a purple background with a login screen. I am certain that it's not a hardware issue.

Ubuntu will not even recognize the on-screen keyboard for input. Therefore I am certain that something has gone bonkers with the OS in some way.

I am not super skilled with Linux, so any tips/tricks will require steps that are very well explained (sorry). I am tempted to use a boot cd, copy data onto a USB hard drive, and then do a fresh install. I was just hoping to not have to do that if this could somehow be easily salvaged.

---

### Post by searchfgold6789 on 2011-09-09
I would go under Keyboard at the login screen and make sure the layout is correct - have it autodetect if necessary. You can do a fresh install using the Alternate download and do the same thing - ocne the installer gets to the keyboard setup part just have it autodetect the keyboard settings.

---

### Post by dino99 on 2011-09-09
boot into recovery mode (hold 'shift' key down at bios end process to see the grub menu): select the 2d line (recovery) then select 'repair package'

---

