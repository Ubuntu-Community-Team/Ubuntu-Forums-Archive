---
title: "update manager appearance"
date: 2011-10-25
forum: General Help
---

### Post by techvish81 on 2011-10-25
whichever theme I keep for windows and menus,  the update manager remains the same as in windows 95( ugly old grey with big square buttons.) 
I am running xubuntu 11.10.
plz help.

---

### Post by oldtimer7777 on 2011-10-25
> **techvish81 said:**
> whichever theme I keep for windows and menus,  the update manager remains the same as in windows 95( ugly old grey with big square buttons.) 
I am running xubuntu 11.10.
plz help.

I've never used xubuntu, but I love Lubuntu.. Have you tried Lubuntu yet? It is small in memory footprint size than xubuntu as well..

Here is a guide.. 
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

---

### Post by crdlb on 2011-10-25
The problem is that update-manager is using GTK3, which has a new, incompatible theme system. At the very least, you should be able to use Adwaita (GNOME 3's theme) for those apps by copying Adwaita's gtk-3.0 folder into your theme.

Ubuntu's Ambiance and Radiance are two of the few themes I know of with GTK2 and GTK3 versions.

---

### Post by gsmanners on 2011-10-25
For anyone wondering, Adwaita is in gnome-themes-standard, and Ambiance and Radiance are in light-themes (both in the repo).

---

### Post by techvish81 on 2011-10-25
ok, thanks for the replies, i will try and comeback with the results

---

### Post by techvish81 on 2011-10-25
problem is solved, i managed to install light themes and they look nice in update manager. thank u all.

---

