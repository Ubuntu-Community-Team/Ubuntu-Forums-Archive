---
title: "Menu persistence problem"
date: 2010-08-01
forum: General Help
---

### Post by fyo on 2010-08-01
I have a really, really weird and exceptionally annoying persistency issue with (primarily) the menu.

10.04 64bit fresh install. All updates installed.

-> Install application.

-> New menu item or submenu appears in Applications menu.

-> Disappears (!!!) on reboot.

-> Menu item / submenu NOT present for other users, even without reboot.


What makes this exceptionally annoying is that it is entirely inconsistent. Sometimes the menu item will "stick" (and if it does, it STAYS), other times the menu item won't even appear in the first place.

Basically, I'm reduced to installing / uninstalling / repeat until the menu item stays.

Anyone with any ideas?

---

### Post by sbrbot on 2010-08-02
I have almost the same problem. My "Applications" menu list disappeared! I really don't know how and why? My ~/.config/menus/applications.menu and /etc/xdg/menus/applications.menu are empty now.

With "System" menu list everything is fine. There is ~/.config/menus/settings.menu pointing to /etc/xdg/menus/settings.menu inside it (XML).

The question is how to restore applications.menu XML file and restore Applications menu items?

---

### Post by sbrbot on 2010-08-02
I had a new installed Ubuntu 10.04 machine so here are applications.menu and settings.menu files from /etc/xdg/menus folder:

HTH

---

