---
title: "gdm: error ..."
date: 2006-04-18
forum: General Help
---

### Post by Skeletonix on 2006-04-18
Hello

I unistalled X-ubuntu-desktop package, then I install ubuntu-desktop package ... set gnome as default sesion! and restarted Pc and...

[I]gdm: error while loading shared libraries /usr/lib/libXcursor.so.1: unsupported version 0 of Verneed record
[/I]

Pleas...What can I do if I wont start X?

---

### Post by Ramses de Norre on 2006-04-18
sudo apt-get install --reinstall libxcursor1 libxcursor1-dbg

---

