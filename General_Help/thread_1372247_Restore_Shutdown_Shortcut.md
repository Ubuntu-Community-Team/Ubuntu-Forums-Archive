---
title: "Restore Shutdown Shortcut"
date: 2010-01-04
forum: General Help
---

### Post by kabeza on 2010-01-04
I'm using latest version of ubuntu, 9.10
I've installed compiz, restricted extras, development software, etc. and something happenned

I noticed the shutdown icon/shortcut next to tray bar clock is missing...

Here is the image so you can understand what I mean
[IMG]http://img683.imageshack.us/img683/4761/shutdownsshot.jpg[/IMG]

I've tried panel properties, but had no luck

---

### Post by J V on 2010-01-04
you mean the one you click to get a list of options?

Try "Add to panel" - they're all there (You might be looking for indicator applet)

---

### Post by kabeza on 2010-01-04
Yes, the one we click to get the list of options to shutdown, reboot, close session, etc..
I don't know what you mean with in your 2nd. line, I can't find a way to restore the icon back... nor where to find it, nor how to add it next to clock

I've found only a shortcut to shutdown, clicked add to panel, but it adds besides the "Applications, Places, System" menu

---

### Post by mcduck on 2010-01-04
> **kabeza said:**
> Yes, the one we click to get the list of options to shutdown, reboot, close session, etc..
I don't know what you mean with in your 2nd. line, I can't find a way to restore the icon back... nor where to find it, nor how to add it next to clock

I've found only a shortcut to shutdown, clicked add to panel, but it adds besides the "Applications, Places, System" menu

The default applet is called "Indicator Applet Session". And once you have added it to your panel you can move it where you want (even to other panels) by dragging with your middle mouse button (or right-click and select "Move" from the menu). If it refuses to move past some other applet right-click that applet and make sure"Lock to Panel" is disabled.

---

### Post by kabeza on 2010-01-04
- lock to panel is disabled
- the only shutdown icon i can add to the panel is not the same i could see before
- i can move the icon but it refuses to move to the most right area... it stops at the beginning of tray area

[IMG]http://img7.imageshack.us/img7/8730/screenshot002cs.jpg[/IMG]

---

### Post by mcduck on 2010-01-04
You have to disable the "Lock to Panel" from all applets that are in the way, not just the one you want to move. So you also need to unlock the Notification Area-applet (the "tray area" you mentioned). Notification Area-applet has a small handle at far left (those three small lines between your shutdown applet and the notification area) that you can click to access the right-click menu for the applet.

And like I said, the default applet is "Indicator Applet Session", not the "Shut Down" you now added to the panel.

---

### Post by kabeza on 2010-01-04
> **mcduck said:**
> ...And like I said, the default applet is "Indicator Applet Session", not the "Shut Down" you now added to the panel.

I would love to know how was the "Indicator Applet Session" translated into spanish, because I don't see it :lolflag:

Anyway, I'll try this when I reach work, and will keep doing some research, and then will update to mark thread solved

---

### Post by kabeza on 2010-01-05
I don't know why, but the indicator-applet-session package was "unchecked" in my synaptic package manager
I've checked, applied, hope it restores back once I reboot

[IMG]http://img121.imageshack.us/img121/1576/screenshot003xd.jpg[/IMG]

**Edit: it worked fine. Now I have the indicator-applet-session back**

---

