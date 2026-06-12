---
title: "problem in minimizing an application"
date: 2011-04-30
forum: General Help
---

### Post by sainath90 on 2011-04-30
[SIZE=2]im using ubuntu 11.04....whenever im opening an application,im unable to see the menu bar and there are no close,minimize,maximize buttons in the left corner of menu bar[/SIZE]

---

### Post by chirag64 on 2011-04-30
Open Compiz Config (CCSM) and enable Window Decoration under Effects :)

---

### Post by sainath90 on 2011-04-30
but after enabling it...the application and files n folder icons r gone in the unity bar

---

### Post by chirag64 on 2011-04-30
Try resetting the unity profile in compiz instead...
enter **unity --reset** in the terminal

---

### Post by texla on 2011-05-01
> **chirag64 said:**
> Try resetting the unity profile in compiz instead...
enter **unity --reset** in the terminal
This happened to me after the last update from Beta2 to current Natty.  All of my top panel buttons from windows (window decorations - I guess they're called) disappeared every time I reduced or unmaximized a window.  This was tough to deal with because then the windows are almost unusable because you can't move them or close/maximize them.  I was using the trick where you hold the alt key down while you hover the mouse over a window and then moving it up and jamming it into the global menu or top panel to force it to maximize.  Gratefully, resetting Unity seems to have fixed all of this.

---

