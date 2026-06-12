---
title: "Lost native resolution after crash"
date: 2009-07-08
forum: General Help
---

### Post by julrich on 2009-07-08
Kubuntu 9.04 64 bit, ATI HD3470 dual head...

I was messing around today, and tried to "switch user" -- BAD IDEA... Screen went blank, and the OS responded to zero commands (ssh didn't work either).  In somewhat of a leap-of-faith, I held down the power button, and shut it off.

Re-booted, and noticed I no longer had my dual 20" monitors working together as one big desktop.  Also, my fonts went back to large size (I had it configured to 75DPI...)  Well, no biggie, I thought -- I tried to re-configure with Catalyst Control Center, and after a reboot, I could no longer get my native 1600x1200 res.  I am stuck at 1024x768 on both monitors, with a max large desktop of 2048x768.  I've tried many things;  Un-installing ubuntu ati-drivers, installing ATI packaged drivers, removing both, installing each other one at a time again.  Manually configuring xorg to force 1600x1200, using the aticonfig command to set resolution, nothing works!  

It seems like somehow, the system just isn't recognizing my monitors anymore.  They are showing up as "generic autodetecting monitor"  with max resolution of 1024x768.  I'm pretty sure that before the crash, they were both identified correctly as Dell 2000FP.

I've tried dpkg-reconfigure xorg, and that doesn't even ask me anything about monitors... Just asks 10 different questions about the keyboard, resets xorg.conf to "vesa", and sends me on my merry way (vesa doesn't work at all by the way...)

Please help, I'm going insane.  ):P

---

### Post by julrich on 2009-07-09
I've managed to get my resolution to 1600x1200, but the whole screen is zoomed in, and the mouse pans around the screen.  Any way to fix my problems?

Thanks

---

### Post by julrich on 2009-07-09
As much as I hated to do it, I re-installed.  This will take forever to get everything back.  I need to find a good backup method.

---

