---
title: "Laptop power management"
date: 2010-06-22
forum: General Help
---

### Post by Yarui on 2010-06-22
I was recently given a fairly old laptop and was told the battery in it didn't work.  I decided to install Debian on it and when everything was set up I tested out the battery.  It has been a while now so I may be mistaken, but I am pretty sure the power stayed on when I unplugged the laptop.  After running Debian on it for a little while I decided to switch it to Ubuntu.  When I was finished installing Ubuntu I noticed there was no battery power Icon in the system tray and when I tested out the battery, power was lost.  Do I need to install something extra for Ubuntu to recognize that I need those power management options, or do I just have to enable it?  Because the battery worked in Debian (I am pretty sure), I figure I probably just need to configure something differently.  Any Ideas?

---

### Post by cbrunhaver on 2010-06-22
you can install the powertop and  laptop-mode-tools from the Ubuntu Software Center should help battery life.  

I don't know what is going on with gnome-power-manager, but you way want to search the forum for more info using those words.  You could try to reinstall the gnome-power-manager package in synaptic, possibly.

---

