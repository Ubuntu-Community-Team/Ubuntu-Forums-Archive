---
title: "Desktop environment vs Window manager"
date: 2010-04-23
forum: General Help
---

### Post by jre6 on 2010-04-23
What is the difference between desktop environment and window manager?

---

### Post by aysiu on 2010-04-23
A desktop environment is the whole interface--toolbars, widgets, windows, window controls, and usually a set of default applications.

A window manager literally just manages the application windows.

Every desktop environment includes a window manager. Gnome includes the Metacity window manager. KDE includes the KWin window manager. Xfce uses the xfwm4 window manager.

You can run a window manager without a desktop environment. But you cannot run a desktop environment without a window manager... well, you *can*, but it wouldn't be useful.

Most people who run just a window manager without a desktop environment do not run Metacity, KWin, or xfwm4.

They tend to run OpenBox, FluxBox, IceWM, Enlightenment, or a bunch of others. You can read more here:
[http://xwinman.org/](http://xwinman.org/)

---

### Post by jre6 on 2010-04-24
Thanks for the information.

---

### Post by Mark76 on 2010-04-24
> **aysiu said:**
> 
Every desktop environment includes a window manager. Gnome includes the Metacity window manager. KDE includes the KWin window manager. Xfce uses the xfwm4 window manager.

Actually, Gnome has only had its own integrated window manager since 2002. Before that it used Enlightenment and Sawfish. Both of which are standalone WMs. Likewise Xfwm has only been part of the Xfce environment since version 4.2.

LXDE is in a similar position to Gnome and Xfce in their early days as it also relies on an external window manager.

---

