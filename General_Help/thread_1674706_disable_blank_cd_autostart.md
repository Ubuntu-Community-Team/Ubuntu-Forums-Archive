---
title: "disable blank cd autostart"
date: 2011-01-24
forum: General Help
---

### Post by izghitu on 2011-01-24
Hi,

I have Ubuntu 10.04 with Gnome. Whenever I put in a blank CD/DVD an icon on the desktop appears named "Blank CD/DVD" and a window appears asking me what I want to do with it.

How do I disable the window and the icon from the desktop?

Please help
Thanks

---

### Post by hhh on 2011-01-24
That should be configurable via gnome-volume-properties. Go to "System->Preferences->Removable Drives and Media->Storage" (or enter gnome-volume-properties in the run dialog) and change the settings under Blank CD and DVD Discs.

---

### Post by izghitu on 2011-01-24
it says "command not found"

what package is it in?

---

### Post by mc4man on 2011-01-24
it's done in File Management which is an option in System > preferences that's not enabled by default
One of many ways
```
nautilus-file-management-properties
```

Look under 'Other Media'

---

### Post by izghitu on 2011-01-24
that worked, thanks a lot

---

### Post by mc4man on 2011-01-24
If you wish to have FM as a menu option than right click on Applications in upper panel > edit menus and under System > Preferences you'll see File Management in the r. side box. Click to enable.

---

