---
title: "Suddenly having very poor performance with 3D stuff; was working fine for a long time"
date: 2011-09-02
forum: General Help
---

### Post by kaldor on 2011-09-02
Using stock Catalyst drivers as shown in Jockey. AMD Radeon HD 6450 512 MB GPU.

I used to do everything on this just fine. Games are now entirely unplayable, and everything feels choppy/laggy. Booting into my Windows 7 partition shows that it is not a hardware problem; I get very good performance with everything on that.

I did not apply any updates or change any settings. I booted up my PC today to find that gaming and other simple things are just downright slow and useless. Rebooting or disabling compiz do not help at all. 

Before, I used to get very smooth gameplay on games such as Quake 4, Quake Live, and Urban Terror. Now, for whatever reason, I can barely play anything. I used to get a consistent 125 FPS on Urban Terror and Quake Live, but now the max I can get is 50 FPS and the mouse feels heavily delayed. This doesn't make sense to me at all; why would it just start behaving like this when I did not change or do anything? Last night I was gaming and doing my normal tasks just fine.

The Top utility doesn't show any processes that are out of the norm. I just want to know what has happened and how I can fix this :(

tl;dr: Massive performance drop with Catalyst drivers. What's going on?

---

### Post by kaldor on 2011-09-02
Sorry for early bump, but I made a bit of a finding here:

```
    $ grep WW /var/log/Xorg.0.log
            (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
    [    23.941] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    [    23.941] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
    [    23.941] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
    [    23.941] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
    [    23.941] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
    [    23.984] (WW) Falling back to old probe method for fglrx
    [    23.987] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
    [    23.987] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
    [    23.987] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:1) found
    [    23.987] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
    [    23.987] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
    [    23.987] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
    [    23.987] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
    [    23.987] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
    [    23.987] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
    [    23.987] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
    [    23.987] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
    [    23.987] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
    [    23.987] (WW) Falling back to old probe method for vesa
    [    23.987] (WW) Falling back to old probe method for fbdev
    [    24.025] (WW) fglrx(0): board is an unknown third party board, chipset is supported
    [    25.502] (WW) Touch X valuator does not match pointer X valuator, pointer emulation may be incorrect
    [    25.502] (WW) Touch Y valuator does not match pointer Y valuator, pointer emulation may be incorrect

```

Thanks.

---

