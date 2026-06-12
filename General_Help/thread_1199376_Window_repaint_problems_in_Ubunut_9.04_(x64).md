---
title: "Window repaint problems in Ubunut 9.04 (x64)"
date: 2009-06-28
forum: General Help
---

### Post by rob4jp on 2009-06-28
Hi Ubuntu users

I have *serious* problems with the graphical interface on my Ubuntu system. After having used the system for a while after logging in on the system (30 min or 1 hour, or so) most applications start to fail to repaint the windows properly. I have this problem with all gnome programs (terminal, nautilus, evolution, the document viewer, just to mention a few), and all KDE programs (kile, okular, qtiplot, to mention a few). Only very few applications do behave properly (for example firefox). 

Anyone who had similar problems? Any solutions out there?

I am using this system in a professional setting, on a high-end workstation and this kind of graphics glitches are completely unacceptable. Its very unfortunate that Ubuntu have these kind of quality problems: the system is otherwise so nice. But this problem is a real show stopper...

I use the 09.04 release of Ubuntu (64 bit version), have a NVIDIA graphics card and I am using the recommended driver (version 180), on a 3.0 GHz quad-core Xeon with 1600MHz memory bus, 16 Gb Ram, etc.

I would appreciate any help/information on this issue.

Best regards
Robert

---

### Post by akakingess on 2009-06-28
If this is happening with both gnome and KDE I might start looking at the hardware/drivers, etc. in particular the graphics card. That's about all the input I can give right now unless we can get some more info and specs to see if there is a confilict.
 
akakingess

---

### Post by rob4jp on 2009-07-16
In the case of someone else having a similar problem, here is a boring but useful work-around:

I deactivated the visual effects (System -> Preferences -> Appearance - Visual Effects), i.e., I selected the "None" option, and I have been experiencing a much more stable system since then. Before I had the default "Normal" option activated. The interface is a bit dull now, without the nice visual effects, but at least it is relatively stable.

I still don't know what caused the problems, but the daily crashes of X and the repainting problem do not happen anymore. Quite likely the previous poster was right, and it is related to the hardware or driver (I am using a nVidia Quadro NVS 290 rev 161 graphics card, with the recommended driver with version 180).

Rob

---

### Post by tom82 on 2009-07-16
For what it's worth, I am having similar (but less severe) repaint problems on 9.04.  I have an NVIDIA card inside my Dell Latitude D620 laptop, and am also running version 180 of the NVIDIA proprietary driver.

I am seeing these repaint issues mostly in gvim (my most frequently used program) but have also seen it a few times in Firefox and Lotus Notes running under Wine.  I haven't tried disabling desktop effects as I find the problem bearable.  (Is easy to force a screen refresh in gvim.)

Best of luck!

---

