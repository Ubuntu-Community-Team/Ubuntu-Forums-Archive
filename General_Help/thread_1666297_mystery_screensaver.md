---
title: "mystery screensaver"
date: 2011-01-13
forum: General Help
---

### Post by Jeek Elemental on 2011-01-13
Ive disabled gnome-screensaver and power manager via preferences->screensaver, but screen goes blank after some interval anyway.

Moving mouse gets screen back, but any wine program that was running is now dead. It also activates when viewing movies/browsing.

This is on ubuntu meerkat 64 bit, all updates.

Anyone have an idea whats going on please?

---

### Post by lithopsian on 2011-01-13
Laptop?  Is the screen dark (on but no desktop) or black (off)?  Some machines will power down their own displays without Ubuntu doing it to them.

There are other screensavers such as xscreensaver but normally you'd have to install them yourself.   Check if anything screensaver-like is running anyway.

---

### Post by Frogs Hair on 2011-01-13
Try System > Preferences > Power Management to view monitor sleep time settings.

---

### Post by coldraven on 2011-01-13
You could check your BIOS settings but if it was not doing this before then that's probably not it.
I think there may be a bug in the Power management settings.
Even though I had "When lid closed" set to "Blank Screen" it would go into shutdown mode.
This seems to be fixed with the latest kernel that auto-updated last week.
However, you could run gconf-editor and look under "apps" "gnome power-manager" to see if the correct settings are reflected there.

---

