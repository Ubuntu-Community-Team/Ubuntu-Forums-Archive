---
title: "Where are panel tray icon image files?"
date: 2011-07-19
forum: General Help
---

### Post by meridionaljet on 2011-07-19
Hello,

I'm on Ubuntu 10.04 Lucid. I need to find the icon image files used by the Gnome panel tray apps, specifically, Banshee (see attached screenshot). It's not in /usr/share/pixmaps, as that banshee icon is used for the panflute launch button, not the Banshee tray icon. I imagine it would be where all the other tray icons are (volume, battery, etc). I'm looking for it so I can try editing it to fix the white background (again see the screenshot) Any help in finding these image files would be appreciated.

---

### Post by CatKiller on 2011-07-19
It's complicated. The icons for the theme you're using are in /usr/share/icons/*themename*, arranged by size and purpose. Themes *inherit* other themes, so if a particular theme has no icon for a particular object, the icon can be taken from a different theme that hopefully fits in. [Here]("http://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html")'s how it's supposed to work.

If it's the application itself putting the icon there, rather than the desktop environment, it could be absolutely anywhere. A look at the list of files installed by the *banshee* package suggests it's put its icons in /usr/share/icons/hicolor and /usr/share/banshee/icons/hicolor.

---

### Post by Frogs Hair on 2011-07-19
Icons may also be found in home/hidden folders/.icons depending how you install them . I found the method for changing icons varies from set to set . I have success with changing application icons that appear on the menu or Unity launcher , but have not tried with panel icons .   In the set I am currently using the panel icons appear in the status folder . If there is no icon for that application provided the application will use its own .

---

