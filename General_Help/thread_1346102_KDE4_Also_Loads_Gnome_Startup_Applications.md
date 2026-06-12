---
title: "KDE4 Also Loads Gnome Startup Applications"
date: 2009-12-04
forum: General Help
---

### Post by daemon3 on 2009-12-04
I like to have applications like Banshee automatically start for Gnome.  However, KDE seems to get the startup apps from the same database.  Is there a way to let just KDE applications to start?  Is this a bug?  Thanks in advance.

---

### Post by seeker5528 on 2009-12-04
The directory '~/.config/autostart' is the standard location for startup items that are not specific to a window manager/desktop environment.

I have not tried this, but it looks like, if you go to 'systemsettings --> advanced --> autostart' and uncheck the items you don't want to start when KDE starts, this will disable them for KDE, but when you go into Gnome they will still start.

In Gnome if you go to 'system --> preferences --> startup applications', 'Gnome login sound' is checked, but it's not checked in systemsettings.  

Later, Seeker

---

