---
title: "A few icon questions"
date: 2009-07-27
forum: General Help
---

### Post by Muscovy on 2009-07-27
I was wondering where the icons are actually defined. Like how in your ~/, Desktop has a different icon. I want to try and add unique icons for those other folders.
  And where is the data from the emblems you've deployed stored? Where does it remember what's been applied?


  Edit: for new icon, I mean across the board all sizes, not just the properties->icon thing.

---

### Post by Diabolis on 2009-07-27
Icons are stored in /usr/share/icons
I don't know where are the emblems and those settings are stored in gconf, but not sure where. You can edit and look at them by executing **gconf-editor**.

---

### Post by CatKiller on 2009-07-27
> **Muscovy said:**
> I was wondering where the icons are actually defined. Like how in your ~/, Desktop has a different icon. 

[http://www.freedesktop.org/wiki/Specifications/icon-theme-spec](http://www.freedesktop.org/wiki/Specifications/icon-theme-spec)

> And where is the data from the emblems you've deployed stored? Where does it remember what's been applied?

~/.nautulus/metafiles, as the <keyword> tag in the appropriate XML file.

---

### Post by jerrrys on 2009-07-27
right click on folder>properties>click on icon  and
 icons are also in file system/usr/share/pixmaps

---

### Post by vinutux on 2009-07-27
icons are stores as root /usr/share/icons

if you installed icons as an normal user its goes to here /home/yourusername/.icons.......(the [COLOR="Red"]dot[/COLOR] of .icons means it is hidden press Ctrl+H for viewing hidden files)

---

