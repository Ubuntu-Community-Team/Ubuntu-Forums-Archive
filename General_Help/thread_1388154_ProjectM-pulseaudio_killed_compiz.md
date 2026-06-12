---
title: "ProjectM-pulseaudio killed compiz"
date: 2010-01-22
forum: General Help
---

### Post by Blackhole454 on 2010-01-22
Ok, here's my problem. I was listening to music in Songbird when I opened up ProjectM-pulseaudio for a visualization. When I hit the F key to put the visualization into fullscreen mode, my screen flashed for a few seconds, then I got kicked back out to the login screen. When I logged back in, Compiz wasn't working, it had switched back to Metacity. I haven't been able to get compiz to start working again since then.

I've tried going into Appearance Preferences and enabling visual effects. A box pops up saying "Desktop effects could not be enabled." I've also tried using the Compiz tray icon to switch the window manager to Compiz. This disables metacity, but doesn't enable compiz. Finally, I tried running the command ```
compiz --replace 
``` in a terminal window. That gives the following output:

```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```
When I close that terminal window, I get the same effect as when I tried switching to Compiz using the tray icon.

In case it helps, here's my computer's specs:
Dell Studio XPS laptop with
Ubuntu 9.10 64-bit
4 GB RAM
Nvidia GeForce 9800M G graphics card with 512MB RAM
Core 2 Duo processor

I've been struggling with this problem for an hour or two, and I'd really appreciate any insight to get it working again.

---

