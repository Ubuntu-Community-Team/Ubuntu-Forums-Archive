---
title: "?? Fresh Install Boots Once But Never Again ??"
date: 2010-01-26
forum: General Help
---

### Post by RRF2525 on 2010-01-26
Greetings --

New to this space and have first install of 9.10 (just pulled from site and burned .iso to CD) on Asus A8N, 2GB, Athlon Manchester (x64), dual XFX GeForce 6800GS GPU's (SLI is BIOS enabled).  Dual booting XP x64 (250GB) w/9.10 on second HDD (1TB cap. w/250GB dedicated w/no other OS on that drive) GRUB is bootloader...

My issues:

1.  Fresh install doesn't recognize Nvidia drivers to set screen res to 1680x1050.  System prompts me to run nvidia-xconfig as root...no luck in doing that.  I have enable the proprietary Nvidia drives for the GPU as recommended.  Ideas?

2.  After reboot the system refuses to come-up.  I get normal POST, GRUB and selection for 9.10.  I get the Ubuntu logo on black then nothing...monitor looses signal and system is unresponsive -- can no longer boot to Ubuntu.  This stinks the most.  Ideas?

3.  Web loads WAY SLOW.  I've read the thread below on this but didn't see anything relating to my situation.  Using DHCP 1G switch over Cat5e to router and out DSL.  MS works fine...Ubuntu is tortise city.  Ideas?

3.  XP still boots but who cares?  I'm trying to get rid of Windows...

Party on dewds!

---

### Post by quixote on 2010-01-28
I'm confused.  It won't boot all the way, but then it runs a browser (even if too slow)?  

The point at which the boot hangs, after the logo, is the point at which the graphical system has to be working.  If it's not, then there's a problem in the configuration of the X windowing system.  If the automated fix for nvidia drivers didn't work, then it may be a matter of editing xorg.conf.  The problems with the graphics configuration is probably also the reason things run so slowly.

If you could explain a bit what your situation is?  Can you or can you not boot?  If sometimes, then is there any pattern to the failures / successes?  

Nvidia graphics can be tricky (because Nvidia doesn't provide specs to the open source community, so building drivers is much harder than it needs to be).  Once it's working, as you know from the MS side, they're well worth it.

---

