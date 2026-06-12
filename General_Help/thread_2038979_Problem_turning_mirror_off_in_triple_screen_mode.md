---
title: "Problem turning mirror off in triple screen mode"
date: 2012-08-07
forum: General Help
---

### Post by ashinms on 2012-08-07
Hi all. I have been running Ubuntu full time for just awhile now, and I am having some odd issues in Ubuntu 12.04. I have three screens (1440X900). I want to turn "Mirror" off and span across three screens, but when I try, I get this: "required virtual size does not fit available size: requested=(4320, 900), minimum=(320, 200), maximum=(1440, 1440)".

WTF is this???? :confused:

I'm not trying to set the resolution of one screen, I'm trying to turn mirror off and display across all three. I have updated my drivers, and  tried all kinds of different configurations. Please help.

---

### Post by QIII on 2012-08-07
You tagged this as "eyefinity" so I assume you have the proprietary ATI fglrx driver installed?

Are you using the Catalyst Control Center or the display settings dialog in Ubuntu?

---

### Post by ashinms on 2012-08-07
Normal dialogue. I only tagged it as eyefinity to give a sense of my setup and to draw people interested in multi-monitor setups, but yes, I do have the proprietary drivers installed. I can't seem to get CCC to install without the instillation hitting a major snag. One thing that could be a factor is that I am running KDE and Unity/Gnome at the same time. I know that it isn't all of my problem, though, because I have been seeing this since before I installed KDE.

---

### Post by QIII on 2012-08-07
How are you trying to install CCC and what snag are you running in to?

You will need to use CCC, since the xorg.conf created as part of installing the driver will dictate the behavior.   CCC modifies xorg.conf.

---

### Post by ashinms on 2012-08-08
I download "Automated installer and Display Drivers for X.Org 6.7, 6.8, 6.9, 7.0, 7.1, 7.2, 7.3, 7.4, 7.5, or 7.6" from AMD's website.

It opens in gedit and gives me a status bar that reads "loading amd-driver-installer-12-6-x86.x86.run from /Software"

When the status bar reaches about 70 percent, just simply closes. Sometimes, I get an error message, but they always say something different.

---

