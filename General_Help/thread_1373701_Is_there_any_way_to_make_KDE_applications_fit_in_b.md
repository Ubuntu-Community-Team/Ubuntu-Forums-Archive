---
title: "Is there any way to make KDE applications fit in better with the Gnome environment?"
date: 2010-01-06
forum: General Help
---

### Post by Macfunky on 2010-01-06
As above. I read some stuff about making Gnome apps fit in with the KDE desktop but not the other way around. I use a few KDE apps and it would be nice to have their themes fit in with my Gnome desktop if possible

---

### Post by mocoloco on 2010-01-06
If they are QT4 apps, then yes.  I'm guessing they're not because by default the QT4 theme uses the GTK+ style by default and they fit in pretty well, so if you're asking they're probably built with QT3.  If they're QT3 apps then there's not a way you can have them use the GTK theme, and the only way to get a unified look is to install a theme that exists for both QT 3 and Gnome, the main one being called qtcurve.  

You can change the look of QT 4 and 3 apps by installing [qt4-qtconfig]("apt:qt4-qtconfig") and [qt3-qtconfig]("apt:qt3-qtconfig").


Oh, in case you didn't know, QT is the toolkit used in KDE, GTK is the one used in Gnome.

---

