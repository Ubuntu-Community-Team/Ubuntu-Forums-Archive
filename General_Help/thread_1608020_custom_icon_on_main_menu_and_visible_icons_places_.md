---
title: "custom icon on main menu and visible icons places and system from gconf-editor"
date: 2010-10-28
forum: General Help
---

### Post by jambel on 2010-10-28
Hi,

I'm trying to change the icon on my custom main menu on Ubuntu 10.10 doing this

> sudo gconf-editor

apps/panel/default_setup/objects/menu_bar

I gave object_type menu-object and custom_icon path as /home/john/Pictures/menu.png then I checked use_custom_icon

but with no luck (notice that I've succeed doing this in a virtual machine with the exact settings)

Also I want to have icons on places and system, so I did this

desktop/gnome/interface and clicked menus_have_icons

what I'm missing?

thanks in advance!

John.

---

### Post by hhh on 2010-10-28
I haven't checked if your other markup is right, but one problem is that you are running gconf-editor as sudo. Don't.

---

### Post by jambel on 2010-10-28
OMG! how did I miss that, thank you man!

---

