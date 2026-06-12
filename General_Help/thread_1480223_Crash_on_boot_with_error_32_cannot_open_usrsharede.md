---
title: "Crash on boot with error 32: cannot open /usr/share/debconf/"
date: 2010-05-11
forum: General Help
---

### Post by Capt2836 on 2010-05-11
Good day

After plugging in an USB stick, I lost all the icons off the desktop (top and bottom toolbars were OK).

Shutdown normally.

On rebooting, shortly after the Eeebuntu splash screen, boot stopped and blue screen came up:

Failed to start the X server.... etc etc

on diagnosing the problem it says:

32: Cannot open /usr/share/debconf/confmodule

Could not generate /etc/X11/xorg.conf.failsafe for vesa driver

Then X server is now disabled. Restart GDM when it is configured correctly.

Then dumped to command line log in.

Have found that a whole lot of what should be folders in /usr/share/ (inc debconf) are now "empty files"

Have tried sudo dkpg-reconfigure -phigh xserver-xorg

No joy - 

How do I solve this problem and get Eeebuntu to run again, please!



Cheers
Kim

---

