---
title: "gdm resolution"
date: 2006-04-14
forum: General Help
---

### Post by DFreeze on 2006-04-14
I don't know if it's a bug, or misconfiguration on my side, but I have a different screen resolution in gdm as the one I set in the GNOME desktop.

I bought a new monitor, with much higher resolution capabilities (21", max. 2048 x something). I put all the possible resolutions in x.conf and could access them fine in my GNOME resolution settings program.
But I want the screen to display 1600 x 1200, and gdm seems to just pick the hightest resolution from x.conf and use that. I can hardly see what I'm typing!

Off course I can just remove the two highest resolution-settings in x.conf, but that's not the point. 

Do I have to configure gdm separately or should it use the same resolution I set in GNOME. Do you think I should file some kind of bug-report for this (in the case that gdm should get the correct resolution by itself)?

---

### Post by zubrug on 2006-04-14
Does your graphics card support the resolutions for your new screen. (jealous) If so you might have to reconfigure your xserver.xorg to detect or input the screens vertical/horizontal rates.
You will need to know the bus ID of your card as well as the Vert/Hor rates. Should be on the back or in the manual.

---

