---
title: "Trouble with graphics (asus ul30vt)"
date: 2011-05-30
forum: General Help
---

### Post by sbsin on 2011-05-30
Since 11.04 I've had lot's of problems and my environment is now a compromise. Considering downgrading to 10.10 where I didn't have those issues but thought I'd ask for help first.

Subset of tings not working:
- Quite often the graphical environment locks up (both unity and classical gnome sessions), I cant move or close windows and I can't interact with mouse. I'm getting errors like: "GLib-GObject-CRITICAL **: g_object_ref:assertion `GDK_IS_WINDOW (window)` failed"

- The nvidia drivers for my graphics card is not working. Nvidia setttings says they aren't in use. And when I run nvidias tool for generating the X configuration X won't start.

- Nautilus is working but consumes lot's of memory and runs really slow.

- Sudden X-restarts

System:
Ubuntu 64bit
(Same problems in 32- & 64bit versions of ubuntu)
Asus UL30VT

---

### Post by wildmanne39 on 2011-05-30
> **sbsin said:**
> Since 11.04 I've had lot's of problems and my environment is now a compromise. Considering downgrading to 10.10 where I didn't have those issues but thought I'd ask for help first.

Subset of tings not working:
- Quite often the graphical environment locks up (both unity and classical gnome sessions), I cant move or close windows and I can't interact with mouse. I'm getting errors like: "GLib-GObject-CRITICAL **: g_object_ref:assertion `GDK_IS_WINDOW (window)` failed"

- The nvidia drivers for my graphics card is not working. Nvidia setttings says they aren't in use. And when I run nvidias tool for generating the X configuration X won't start.

- Nautilus is working but consumes lot's of memory and runs really slow.

- Sudden X-restarts

System:
Ubuntu 64bit
(Same problems in 32- & 64bit versions of ubuntu)
Asus UL30VT

Hi , if you activated the driver then it is using it that is a bug that says it is not using it, so if you installed the driver also from another source they might be conflicting. There should be 2 in there for your card I had to use the 173 driver because the new one caused me problems just like you describe.

---

### Post by linuxinstalledfromhdd on 2011-05-30
I would just continue with the process of downgrading.  Seriously, we have gone over this for a few days, if something would work, we would have heard from someone by now.  Unfortunately, the latest version fo Ubuntu isn't always the best solution for everybody.  I truly wish it was though. :) 

Here is a nice walkthough for 10.10 to at least save you some time with your efforts:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

