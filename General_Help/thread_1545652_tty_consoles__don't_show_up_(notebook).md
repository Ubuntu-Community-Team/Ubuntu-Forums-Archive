---
title: "tty consoles  don't show up (notebook)"
date: 2010-08-04
forum: General Help
---

### Post by mexicanseaf00d on 2010-08-04
I'm having trouble giving the right title.. 

The problem is: CTRL-ALT-F1 etc does not give me the login consoles and i strongly suspect it has something to do with the notebook display adapter (a problem on its own, but in this case it seems to be the INTEL GMA).

After pressing the key combo, the HD is working on something, but all I get is a frozen picture of my current (tty7) Desktop. After hitting CTRL+ALT-F7 it blacks out for a moment, comes back to normal gnome Desktop as if nothing happened.

I tried setting different vga modes in grub (according to my research, this also sets tty consoles modes ?) with no luck.

The output of 'hwinfo --framebuffer' is as follows (if it's of any help):
```
02: None 00.0: 11001 VESA Framebuffer
  [Created at bios.464]
  Unique ID: rdCR.7IS+B23HFDE
  Hardware Class: framebuffer
  Model: "Intel(R)Ironlake Mobile Graphics Controller"
  Vendor: "Intel Corporation"
  Device: "Intel(R)Ironlake Mobile Graphics Controller"
  SubVendor: "Intel(R)Ironlake Mobile Graphics Chipset Accelerated VGA BIOS"
  SubDevice: 
  Revision: "Hardware Version 0.0"
  Memory Size: 31 MB + 960 kB
  Memory Range: 0xb0000000-0xb1feffff (rw)
  Mode 0x0360: 1366x768 (+1408), 8 bits
  Mode 0x0361: 1366x768 (+2752), 16 bits
  Mode 0x0362: 1366x768 (+5504), 24 bits
  Mode 0x0363: 1600x900 (+1600), 8 bits
  Mode 0x0364: 1600x900 (+3200), 16 bits
  Mode 0x0365: 1600x900 (+6400), 24 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```

Any ideas, gentlemen?
[I]
other info:[/I]
ubuntu 10.04, gnome, basic compiz settings enabled
HP DV7 4013eg Notebook, intel i5, ATI mobility 5650 (without working drivers)

---

### Post by dragos240 on 2010-08-04
Sounds like it's looking for another monitor to me, even if that monitor is non-existent. If you need to use a tty terminal it looks like you'll need to stop X on boot. See if that helps. Stop the gdm daemon at boot, and see if you are prompted with a tty terminal. If not, we'll try to help your from there.

---

### Post by mexicanseaf00d on 2010-08-04
I usually do not use these terminals, but if something goes wrong I'd be stuck..

Couple of days ago I copied some settings from my PC to this Notebook (like tomboy, evolution folders), which i had to do with gdm turned off. That's when i noticed the bug, and had to ssh into the notebook to do that (which was great success for me, as a newbie).


Where do I configure GDM not to boot? In Grub?

edit: does this still apply [http://ubuntuforums.org/showthread.php?t=1420480](http://ubuntuforums.org/showthread.php?t=1420480)

---

### Post by mexicanseaf00d on 2010-08-05
I haven't the slightest, but it works now

GRUB_CMDLINE_LINUX_DEFAULT="splash vga=771"
matching:
GRUB_GFXMODE=800x600

i also did:
/etc/initramfs-tools/conf.d/splash
with content: FRAMEBUFFER=y
(found this somewhere here on the forums)

---

