---
title: "How to get back System Tray?"
date: 2011-06-18
forum: General Help
---

### Post by ssreddy555 on 2011-06-18
"HPLIP Services detects no System Tray. Not starting. Exiting."

This is the message I get each time on starting the system. 

Yes, the HPLIP icon disappeared from top right. 

How to get it back?

---

### Post by Frogs Hair on 2011-06-18
What version of Ubuntu and is the system tray missing or not detected for some reason ? HPLIP is printing related on my machine , are we thinking of the same thing ?

---

### Post by Matt__ on 2011-06-18
Dont worry about it, HPLIP is still there ready to use, it's only the panel icon that's failed.

Go to startup applications and uncheck hplip. Next, install hp toolbox from software center.

You can then add the hp toolbox link from your preferences menu to whatever dock you are using/desktop/other panel/unity launcher. (I'm assuming you have removed one or more panels from your desktop and use a dock or have removed/modified the indicator applet which is why you get the warning pop-up?)

---

### Post by ssreddy555 on 2011-06-18
> **Matt__ said:**
> Dont worry about it, HPLIP is still there ready to use, it's only the panel icon that's failed.

Go to startup applications and uncheck hplip. Next, install hp toolbox from software center.

You can then add the hp toolbox link from your preferences menu to whatever dock you are using/desktop/other panel/unity launcher. (I'm assuming you have removed one or more panels from your desktop and use a dock or have removed/modified the indicator applet which is why you get the warning pop-up?)

I did this already but i'm curious to know where the System Tray has gone & how to get it back.

---

### Post by ssreddy555 on 2011-06-18
> **Frogs Hair said:**
> What version of Ubuntu and is the system tray missing or not detected for some reason ? HPLIP is printing related on my machine , are we thinking of the same thing ?

HPLIP (HP Linux Imaging & Printing) on any machine is, of course, printing related software.

Ubuntu version is 11.04. I use Classical interface.

---

### Post by ssreddy555 on 2011-06-19
Well, I finally managed to get the system tray back.

It's actually very simple.

Right click on the upper panel >> Add to Panel

In the pop up menu, navigate to Notification Area & add it.

Make sure in the start up applications menu in System >> Preferences, "HP System Tray Service" is ticked.

On reboot, HP icon reappeared in the system tray.

---

