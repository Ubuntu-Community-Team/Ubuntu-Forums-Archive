---
title: "Gnome-do Won't Show Firefox Icon"
date: 2009-08-18
forum: General Help
---

### Post by alligoodw on 2009-08-18
I'm using Ubuntu (Karmic Koala Alpha 4).  Gnome-do will load Firefox, but when selected, it doesn't show Firefox icon.  It's a small problem but one I would like to fix.

Where does Gnome-do look for application icons?  If I know this, I might be able to fix it manually.

Note:  Using Firefox 3.5.2.

---

### Post by CatKiller on 2009-08-19
I've never used gnome-do, but AWN (and everything else for that matter) stores the launcher configuration as [.desktop files]("http://www.freedesktop.org/wiki/Specifications/desktop-entry-spec"). AWN stores its launcher configuration at ~/.config/awn/launchers. Perhaps gnome-do stores them in a similar location? You can either specify the icon to use as an absolute path (like */usr/share/pixmaps/firefox-3.5.png*) or as a theme-dependent relative name (like *mozilla-firefox*).

---

