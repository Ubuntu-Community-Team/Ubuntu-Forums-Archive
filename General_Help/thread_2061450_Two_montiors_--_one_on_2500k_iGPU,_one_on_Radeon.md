---
title: "Two montiors -- one on 2500k iGPU, one on Radeon"
date: 2012-09-22
forum: General Help
---

### Post by axFelix on 2012-09-22
Hey there,

I'm relatively new to Linux, so please bear with me. I've just built a new machine with Ubuntu 12.04, a 2500k, and, as of yesterday, a Radeon 7850.

I had been using the 2500k iGPU with two monitors -- one on DVI, on on VGA -- which Ubuntu recognized and configured just fine. The Radeon has one DVI-D, one HDMI, and two mini-DPs -- one I buy some mini-DP-to-DVI dongles, I should be able to plug multiple monitors into the Radeon, but for the time being, I wanted to try to connect both of my monitors via DVI -- one into the Radeon's DVI-D, and one into the DVI out I had been using on the 2500k. This works fine on Windows.

What's been happening so far on Linux is that the main display attached to the Radeon works fine, and the display plugged into the iGPU is never recognized by Ubuntu and never receives any output apart from -- bizarrely -- when it displays the shutdown indicator. This, though, at least indicates that it's being recognized by the BIOS.

I've been reading lots of threads in the past 24h claiming that running X across two different video devices is difficult to the point of not being possible. This thread ([http://ubuntuforums.org/showthread.php?t=1977473](http://ubuntuforums.org/showthread.php?t=1977473)) gave me hope, but on trying to duplicate it in my xorg.conf (attached), I'm getting the same thing as before -- only with buggier 3D performance. At one point, I tried enabling xinerama, but that failed to improve anything and caused the Ubuntu displays application to quit with an XRANDR error, so I disabled it again. Should I just give up and buy a couple of monoprice dongles, and content myself that my iGPU is going to go to waste as long as I have a discrete card?

Thanks.

---

