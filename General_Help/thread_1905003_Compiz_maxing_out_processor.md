---
title: "Compiz maxing out processor"
date: 2012-01-05
forum: General Help
---

### Post by ArcherB on 2012-01-05
I'm running 11.10 on a quad core AMD 965 with an AMD 6800 series graphics card and 4 GB RAM.  After running the system for a while, I notice my processor fan start to crank up.  I run top to find out that compiz is using up 25% of the processor (100% of a single processor) and will not die.  I tried kill -9 (PIDNumber), no effect.  I tried killall compiz, no effect.  I even tried running both under sudo with no effect.  Killing and restarting lightdm won't kill it.  My only hope is to reboot the entire thing.  

I suspect the video driver may be the issue, but I'm running the one that was installed under restricted drivers.  There are two options in there; AMD graphics and AMD graphics with updates.  The one with updates will not install.  Not that I care, I'm just tired of hearing my fan scream until I give up and reboot into Windows.

Thanx for any suggestions.

Here is how I fixed it:
Downloaded the latest ATI driver from AMD.  I had to search for it specifically as the home page menu only took me to the 11.11 version of the driver.  The latest is 11.12.  I removed all the Radeon drivers using synaptic, rebooted (probably unnecessary), then removed the FGLRX drivers using synaptic, rebooted, installed the 11.12 version of the drivers I downloaded earlier from either SoftPedia or AMD/ATI. 

I must note that after the second reboot, the one after removing the fglrx driver, the screen was flickery, even at the console level and difficult to follow.  After the third reboot, the one after installing the 11.12 driver, everything was fine.

---

