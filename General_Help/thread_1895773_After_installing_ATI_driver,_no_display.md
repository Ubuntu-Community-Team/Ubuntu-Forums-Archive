---
title: "After installing ATI driver, no display"
date: 2011-12-15
forum: General Help
---

### Post by brec on 2011-12-15
10.04

Installed fglrx, ATI/AMD proprietary graphics accelerator driver to use with my Radeon HD 5970s.  Now on startup after the initial generic Ubuntu display (with the five sequencing dots underneath) where I formerly had a GNOME login screen, now there's no screen at all -- just a blank.  Fortunately I had VNC access set up and am using it to access the system via my customary Gnome desktop.  (I notice also now that the Chromium browser displays "Starting Chromium Web Browser" in the panel for several seconds, then unceremoniously quits.)

Of course I can try removing the driver but I'd like to use it.  Any thoughts on what I might do?

---

### Post by brec on 2011-12-15
Uninstalled fglrx, downloaded latest Catalyst package from AMD site, ran its installer.  Everything is now working OK.

---

### Post by Mark Phelps on 2011-12-15
That was quck!  Glad to hear it was so easily solved.  Please use the Thread Tools at the top of the thread to mark this as SOLVED.  thanks

---

### Post by brec on 2011-12-15
> **Mark Phelps said:**
> That was quck!  Glad to hear it was so easily solved.  Please use the Thread Tools at the top of the thread to mark this as SOLVED.  thanks
Done!

Meanwhile, here's a little more detail in case someone finds this thread via Google, etc....

I performed the scorched-earth fglrx removal and ATI re-installation  procedure [described here]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver"), but it didn't solve the problem.  Instead, I got a startup error report saying> 
Ubuntu is running in low-graphics mode
Failed to load module "fglrx" (module does not exist, 0)
No drivers available

which had me scratching my head.  But I was given various options, including starting a session in the low-graphics mode.  I poked around some and found that /etc/X11/xorg.conf was still assuming fglrx (!?).  Since retreating had failed, I decided to try advancing.  I went to [AMD's graphics drivers download site]("http://support.amd.com/us/gpudownload/Pages/index.aspx") and downloaded the current Catalyst package for my hardware (Radeon HD 5970) and also saved and followed the instructions in the release notes, a PDF linked to on the software download page.

Note to newbies:  most system software removal or installation commands issued at the terminal must be preceded by "sudo ", which will generate a prompt for an administrator's password.  This includes the "sh ..." command used to install AMD's Catalyst driver and controller (configuration) package.

Finally, a "sudo reboot" and I was back in business.  The Chromium browser now works again, too.

---

