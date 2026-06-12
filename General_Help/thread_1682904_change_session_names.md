---
title: "change session names"
date: 2011-02-06
forum: General Help
---

### Post by xeemo on 2011-02-06
I'm going to be installing a few GUIs and I wanted to change the text "Ubuntu Desktop Edition" on the login screen (under sessions) to "Gnome".  I've done this before, but I don't remember what config file this info is in.

---

### Post by Krytarik on 2011-02-06
The respective *.desktop files are in "/usr/share/xsessions":

- press Alt+F2
- enter "gksudo gedit"
- browse to the given location
- etc.

[http://library.gnome.org/admin/gdm/stable/configuration.html.en#sessionconfig](http://library.gnome.org/admin/gdm/stable/configuration.html.en#sessionconfig)

---

