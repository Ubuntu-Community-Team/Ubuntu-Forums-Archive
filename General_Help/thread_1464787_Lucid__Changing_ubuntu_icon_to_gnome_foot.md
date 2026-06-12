---
title: "Lucid:  Changing ubuntu icon to gnome foot?"
date: 2010-04-28
forum: General Help
---

### Post by The_Jorge on 2010-04-28
[SIZE=2]Hello, I am using ubuntu 10.04 (Lucid Lynx).  I have tried to change the ubuntu icon to the gnome foot using methods posted for earlier versions to no avail.  Does anyone here know how to change the gnome icon next to the applications menu to the gnome foot in lucid?

Thanks ahead of time.
[/SIZE]

---

### Post by nEx-1 on 2010-05-04
Hi,

I have to update the Icon Cache in my Case....

Changed Gnome-Foot Icon in /usr/share/icons/gnome....  so I have to 

1.  "sudo gtk-update-icon-cache --force /usr/share/icons/gnome/"
2.  "sudo killall gnome-panel"

Et Voila ;)

Greets
nEx

---

### Post by kerry_s on 2010-05-04
you can just use gconf-editor to set a custom icon, it'll be in the panel section.

---

