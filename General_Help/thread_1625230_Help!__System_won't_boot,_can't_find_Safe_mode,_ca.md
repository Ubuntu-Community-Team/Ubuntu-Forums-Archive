---
title: "Help!  System won't boot, can't find Safe mode, can't launch Recovery mode"
date: 2010-11-18
forum: General Help
---

### Post by yaddoshi on 2010-11-18
I attempted to install Catalyst 10.11 for my ATI HD 2600XT and the system now only displays lines and a large block of pixels where the mouse would go.  CTRL-ALT-F1 kills the system and does not provide a command prompt.  This is a single installation, not dual-boot, but there is no Press Esc to access the Grub menu during startup so I cannot choose safe mode.  I attempted to get into Recovery mode using the flash drive that I used to install the system and it tells me there is no Recovery kernel (I used the 64-bit Desktop installer, not alternative).

Does anyone know an alternative to get into the Grub menu other than ESC during bootup?  Alternatively, do I need to download the 64-bit Alternative ISO and create a new boot disk with it so I can access Recovery mode?  Is there something else I'm not thinking of?  My system is currently unusable and I'd prefer to not have to wipe it out in order to fix this.

Thank you in advance.
- Mat

---

### Post by io5cml4z on 2010-11-18
Try using a super grub CD to boot the system.

---

### Post by yaddoshi on 2010-11-18
> **Hoot215 said:**
> Try using a super grub CD to boot the system.
Didn't know there was such a thing, looking into it now - thanks for the tip!

---

### Post by yaddoshi on 2010-11-18
Hoot216 - that did the trick.

In case anyone else runs into this sort of issue - on another system I installed unetbootin (sudo apt-get install unetbootin in Ubuntu) and there is a Windows version available also.

In unetbootin's ISO drop-down menu is the option Super Grub Disk - it's only 1.4MB in size and the program will automatically download it and write it to your USB flash drive.

I booted from that, was able to use the ROOT LINUX option to gain access to a command prompt with network support.  I then followed the Removal directions here to get the system reverted back to the open source ATI drivers again:  [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)

By the way - my wallpaper is a white and brown feathered barn owl on a frozen treebranch - ironic that your handle is Hoot215 - thank you again!

---

### Post by io5cml4z on 2010-11-19
No problem. And that is ironic lol. :popcorn:

---

### Post by arpanaut on 2010-11-19
FYI:  Hold down SHIFT to display the menu during boot (formerly ESC in GRUB legacy).

A little late but might be helpful in the future, or to someone else.

---

