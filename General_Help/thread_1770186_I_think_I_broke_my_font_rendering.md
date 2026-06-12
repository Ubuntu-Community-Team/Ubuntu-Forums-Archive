---
title: "I think I broke my font rendering"
date: 2011-05-28
forum: General Help
---

### Post by ibrabeicker on 2011-05-28
I was messing around trying to use KDE 4 on my gnome unbuntu but firefox looked awkward, so I did a bit of research and installed kde-config-gtk, derived from qt-gtk-engine to make it a bit similar to the rest of KDE, but didn't got the result I was expecting

but when I switched back to gnome session, firefox and chrome's fonts were weird, just like when you are using a stretched 4x3 screen on a widescreen monitor. I removed the package but I suspect when it installed it changed some configuration that persist afterwards

the rest is normal, libreoffice, netbeans etc, just chrome and firefox

any suggestion?

---

### Post by blueridgedog on 2011-05-28
Is the problem evident if you log in as another user?  It may be a config issue in your gnome settings.

---

### Post by ibrabeicker on 2011-05-29
> **blueridgedog said:**
> Is the problem evident if you log in as another user?  It may be a config issue in your gnome settings.

the font is ok in the user i just created.

Any Idea of where is the config file?

EDIT: I deleted the following folders with no success

.gnome-2
.gconf
.confd
.kde
.mozilla

---

### Post by blueridgedog on 2011-06-01
Those were the directories that I would have suggested you delete.  Alternatively, you can backup any files in your home directory then delete the user account and recreate it.

---

