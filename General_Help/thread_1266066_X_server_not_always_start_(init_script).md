---
title: "X server not always start (init script)"
date: 2009-09-14
forum: General Help
---

### Post by yocec on 2009-09-14
In order to make a HTPC / Backup server I bought a d945gclf2 card and I installed a Jaunty command line system


My HTPC software is freevo, wich launched with -fs option launch itself X server


To start freevo at each boot I made a init script (see attachments).

The problem is that freevo don't start each time, because x server don't start.


It's occure randomly each 2 or 3 boot...


In the xorg.0.log file I can see that : 


(WW) intel(0): No outputs definitely connected, trying again...
(II) intel(0): Output VGA disconnected
(II) intel(0): Output TV-1 disconnected
(WW) intel(0): Unable to find initial modes
(EE) intel(0): No valid modes.
(II) UnloadModule: "intel"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules//libvgahw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found



for information, my D945GCLF2 card is pluged with SVIDEO output to SCART input of  my old CRT TV .

I use the last xserver-xorg-intel-video driver in order to correct the known problem with s-video output on this card.


init script has been registered with update-rc.d with default and 99 as level : 

update-rc.d freevo defaults 99



At last, when boot is complete if I launch the init script it's ALWAY works


Why is it "random", why not at all boot ?
Why only during init ?

Why xorg don't find my TV ?

What can I do, change the level (upgrade-rc.d) ?
Add a timer ?


Thanks

---

### Post by yocec on 2009-09-15
no one ?
is it so strange ?

---

