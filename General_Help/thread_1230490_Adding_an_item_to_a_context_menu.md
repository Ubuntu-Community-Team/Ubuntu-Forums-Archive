---
title: "Adding an item to a context menu"
date: 2009-08-03
forum: General Help
---

### Post by Volt9000 on 2009-08-03
Is there a way to add menu items to context menus? For example, in Nautilus when I right-click a file, insert my own menu item? 

I'm not talking about file associations, click right-clicking a file gives me options for different text editors.. I'm talking about a completely separate menu item that I can add, for every right-clicked file, not just specific ones.

---

### Post by SPr on 2009-08-03
I believe context menus in Gnome can only be customised by adding scripts to ~/.gnome2/nautilus-scripts/ These show up in the context menu under the submenu "Scripts".

---

### Post by mc4man on 2009-08-03
In addition to nautilus scripts there is nautilus-actions which will appear directly in the lower context box. ( sudo apt-get install nautilus-actions

You can create many useful actions or find premade ones

Things that can't be done in either may be possible as a nautilus extension which are much more difficult to create and add. ('much' is an understatement

---

### Post by Volt9000 on 2009-08-03
Ok, thanks guys.

---

