---
title: "Kubuntu 9.04 - Dual Monitor Issue."
date: 2009-11-23
forum: General Help
---

### Post by Roasted on 2009-11-23
Setting up Kubuntu 9.04 64 bit on my main computer. Running 180 Nvidia drivers. This machine works perfectly fine with Ubuntu 9.04 64 bit, but Kubuntu 9.04 doesn't detect the proper resolution for my second monitor.

The proper resolution is 1440x900. In the Nvidia-Settings control panel, the highest I can set it to is 1360x768.

Again, no issues in Gnome. Why the issue in KDE?

EDIT - Okay, several updates:

With 173 drivers, the only available resolutions for my 19 inch 1440x900 native res monitor was 320x240 and 640x480 or something like that. With 180 drivers, I have many more options, but the highest is 1360x768 as I said above. In both instances, I still can't get to 1440x900 like I should. In Gnome I can with 180 drivers, in KDE I cannot with 180 drivers.

So I copied my xorg.conf from Ubuntu and threw it in to my Kubuntu system, again same hardware, same computer, dual boot. And it works.

So this is working now, but it brings up the obvious question - what's different about KDE that made it backfire? Linux is Linux. Ubuntu is Ubuntu. No matter what manager it is I would think it would still work with the Nvidia drivers associated with it. What happened?

---

