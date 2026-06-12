---
title: "Headless 10.10 Server force 800x600 resolution"
date: 2011-01-13
forum: General Help
---

### Post by divergex on 2011-01-13
Hi I have set up an Ubuntu 10.10 system and would like to use it as a headless file and print server for several PC laptops and a MacBook. I know that most recommend not using a GUI for a headless server, but I prefer to use it. I have previously tried Ubuntu Server with eBox (Zentyal) and had issues with CUPS configuration settings being lost repeatedly, and also tried webmin but I still prefer the standard Gnome desktop.

Here's my issue. I can boot the system fine without a monitor or keyboard, and I use Chicken of the VNC on my Mac to control it. The only issue is that it defaults to a 1024x768 resolution, I believe because on boot there is no monitor attached. I would like it to default to 800x600 instead.

Through VNC I can't change it from the Monitors preferences because there is no physical monitor so all the choices are disabled. If I connect a monitor and set it to default to 800x600, it still reverts to 1024x768 once I reboot without a monitor.

The computer is an old E-Machines T3410, AMD single core with NVidia integrated graphics, but I have not installed any proprietary drivers because on a previous install with the proprietary driver the boot would not complete without a monitor attached.

Any suggestions?

---

