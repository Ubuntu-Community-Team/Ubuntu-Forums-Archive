---
title: "adding shutdown to the main menu"
date: 2010-05-07
forum: General Help
---

### Post by unebaguettesvp on 2010-05-07
hi-

i miss having a shutdown button in the gnome main menu (not the menu bar). if you right click on the icon for gnome main menu and click "Edit Menus", it opens up alacarte and you can add/edit/delete menu items.

i want to add the shutdown menu item. so, i click "Add Item". my question is, what is the command to open the shutdown window? the application that asks you if you want to shutdown or restart?

thanks for your time!

---

### Post by kerry_s on 2010-05-07
in a terminal type "gnome-session-save --help" or "man gnome-session-save", sorry i don't use gnome so can't remember the exact command to tell you.

---

### Post by rnerwein on 2010-05-07
hi

that's it i think ( i use it by myself )
# aks for shutdown the system
/usr/bin/gnome-session-save --shutdown-dialog

ciao

---

### Post by unebaguettesvp on 2010-05-08
Perfect! Thank you both!

---

