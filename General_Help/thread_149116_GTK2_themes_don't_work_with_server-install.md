---
title: "GTK2 themes don't work with server-install"
date: 2006-03-23
forum: General Help
---

### Post by Jessevl on 2006-03-23
Hello, I installed Ubuntu using the server install instead of the normal one, because iwanted to decide which programs would be installed myself. I installed x-window-system-core, gnome-core and gdm. Everything works fine except for the GTK2 themes, when I apply a theme, the windowborders change, but the buttons and other gtk things change to the standard ones (not the human ones, but the not rounded grey things). The only theme that does work is the standard human theme. Does anybody now how to fix this? or which package I forgot?

---

### Post by Jessevl on 2006-03-24
*bump*

---

### Post by Sutekh on 2006-03-24
*Could* be this one; libgtk2.0-0

[http://packages.ubuntu.com/breezy/libs/libgtk2.0-0](http://packages.ubuntu.com/breezy/libs/libgtk2.0-0)

It seems to be a dependancy for a lot of GTK applications/engines

---

### Post by mcduck on 2006-03-24
make sure you have installed all gtk2-engines that your themes use.. Without those themes won't work :)

(search 'engine' in synaptic)

---

