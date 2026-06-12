---
title: "Cannot change wallpaper"
date: 2010-03-12
forum: General Help
---

### Post by hwttdz on 2010-03-12
If I change the wallpaper using "gnome-appearance-properties -p background" (also reached through system->appearance->background or right click on desktop->change desktop background) there is no effect and I get a "(gnome-appearance-properties:16021): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed" suggestions?

I checked to make sure compiz wasn't somehow screwing with the background by first trying to set a background using the wallpaper plugin then doing killall compiz.real && metacity.  So I should be using metacity at the moment.

---

### Post by hwttdz on 2010-08-13
I'm not sure if this is related, but occasionally I seem to have nautilus selectively hang.  I can still file browse, but I cannot see the desktop icons or change the wallpaper, killall nautilus I believe causes it to respawn, and that seems to fix the problem, however I'm not 100% that's the same issue I was having previously.

---

