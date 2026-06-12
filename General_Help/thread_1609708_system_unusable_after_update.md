---
title: "system unusable after update"
date: 2010-10-30
forum: General Help
---

### Post by pavan115 on 2010-10-30
Hi Wise Ubuntu masters - I need your wisdom!

I was using 10.04 LTS version on my old computer, and decided to make a few software changes - and now my system is unusable. 

This is a summary of what I did - not sure which one messed it up:

1. Uninstall Evolution, rythmbox
2. Install banshee
3. Run updates - got errors similar to this:

[http://ubuntuforums.org/showthread.php?t=1221323](http://ubuntuforums.org/showthread.php?t=1221323)

I tried to fix one of those keys and then went ahead with upgrade. Upgrade got me a new display driver (xserver-intel or something like that) and a new kernel 2.x.25.

rebooting caused the system to boot into a system that only showed background - no panels, nothing. I was not able to do Alt+F2 to run anything either. Mouse was working at this point.

To make matters worse, I did Ctrl+Alt+BACKSPACE (enabled this before) and logged out - saw my login screen, and changed session from Gnome to Failsafe Gnome. Now Everytime I log on, I am stuck at a blank screen.

What I have tried after this:

using the "recovery..." option from Grub, fixed broken packages, and :

- sudo apt-get remove ubuntu-desktop
- sudo apt-get install ubuntu-desktop
- sudo apt-get install evolution
- ran something similar to Xorg -configure

The problem is still there. When I "startx" from failsafe mode, I can see the desktop again, but not my cursor etc.

I could probably reinstall my system from scratch and reinstall everything, but I want to keep this as a last resort.

Any ideas? - Thank you

---

### Post by Quackers on 2010-10-30
I did the same some time ago. I'm not sure if the circumstances are quite the same and whether you've run everything I did to fix it, but have a look here.

[http://ubuntuforums.org/showthread.php?t=1559996&highlight=catastrophe](http://ubuntuforums.org/showthread.php?t=1559996&highlight=catastrophe)

---

