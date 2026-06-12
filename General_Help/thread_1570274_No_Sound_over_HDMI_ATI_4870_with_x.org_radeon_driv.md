---
title: "No Sound over HDMI ATI 4870 with x.org radeon drivers"
date: 2010-09-07
forum: General Help
---

### Post by eukatech on 2010-09-07
Hi!

My first post here, to start im still a n00b when it comes to ubuntu but im trying!

Here's my question: I have Ubuntu Lucid and have an ATI 4870 card which im running with the xserver-xorg-video-radeon display driver.
My videocard is hooked up to an amplifier through HDMI, which with the proprietary FGLRX graphics driver the sound works fine.
Now im running the xorg display driver because the tearing of the FGLRX driver is unbearable when watching SD or HD content on my tv. 
The tearing and lack of vsync are gone with the xorg driver but now i have no sound.

Any help would be greatly appreciated,

eukatech

EDIT: I have tried letting KMS work for me by adding a line in the grub menu.lst (radeon.modeset=0) no join
      and by adding a few lines in xorg.conf (Option "Audio" "On" / Option "HDMI" "all") still nothing :(

---

