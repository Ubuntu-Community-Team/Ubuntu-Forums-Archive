---
title: "Broken Desktop"
date: 2006-06-10
forum: General Help
---

### Post by Xilon on 2006-06-10
I can't remember why but I turned off "Show destkop" in gconf-editor under Apps > Nautilus > Desktop > Preferences which just switched of fteh destkop so the icons didn't render there anymore... but then I wanted it back and toggled it back on but the desktop didn't show up. Since then I have also restarted the PC but still nothing :(

---

### Post by starkes on 2006-06-10
seems like this could happen pretty easily. i've been messing around with gconf-editor myself.

i think gconftool is something that could do the work of gconf-editor but through the command line. Though i dont know how to use it, some googling might do the trick.

---

### Post by starkes on 2006-06-10
found some more info

[http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/)

and i took a look, it seems like you can edit the file called %gconf-tree.xml in /etc/gconf/gconf.xml.defaults/

search for stuff in there, I think thats where you'll find it

---

### Post by Xilon on 2006-06-10
That didn't really help since that xml file only contained stuff for Compiz

Edit: Ok I don't know wth  happend but the desktop has shown up again :|
Edit2: No... it's worse now, I can see the icons for my drives but the desktop isn't mine... it's root's :(

---

### Post by Rui Pais on 2006-06-10
hi, 
have you tried to logout gnome and on a console do
```
sudo rm -rf .gconf* && sudo rm -rf .gnome*
``` and then login at gdm again?

---

### Post by Xilon on 2006-06-10
Yeah that worked, too bad it was at the cost of all my settings :P
Thx.

---

