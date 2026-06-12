---
title: "How to remove icons from menus"
date: 2011-06-08
forum: General Help
---

### Post by Calcipher on 2011-06-08
I installed some software today which has made all of my menus (right click, places, system, the network manager, etc.) start having icons.  Is there a way to turn those back off?

---

### Post by Calcipher on 2011-06-08
I finally tracked down a solution to this.  If you wish to disable menu icons in Ubuntu you need to toggle a key in gconf.  The Key is desktop/gnome/interface/menus_have_icons (set to false to disable).  You can either use the gconf-editor to do this or enter the following command:

```
> gconftool-2 --type Boolean --set /desktop/gnome/interface/menus_have_icons False
```

---

