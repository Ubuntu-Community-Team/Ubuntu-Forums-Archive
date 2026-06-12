---
title: "How to do things as root in GUI mode?"
date: 2009-11-09
forum: General Help
---

### Post by amylase on 2009-11-09
Hi,

I'm cutting and pasting and editting a handful of system files eg. (/var/www). In command line I can happily sudo and do things the way I like but if I try to do similar actions in GUI, the system doesn't let me drag files into restricted folders or modify files in restricted folders. I end up bringing all the files to my desktop, do what I wanted with them, save onto desktop, go to command line and sudo copy them over to desired system directories. This entire process is a pain.

Hope my question is clear: I wish to be able to move files around, edit, save, erase files as root where-ever and whenever, when I operate at graphic user interphase level. How do I enable this with Ubuntu 8.10? Thanks.

---

### Post by benj1 on 2009-11-09
```
gksu gedit
```
to launch gedit as root
```
gksu nautilus
```
to launch nautilus as root

etc
etc

---

### Post by Bucky Ball on 2009-11-09
In a terminal:

```
gksudo nautilus
```

... if you are using gnome.

---

