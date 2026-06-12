---
title: "Problem when i update"
date: 2012-07-12
forum: General Help
---

### Post by pd96 on 2012-07-12
hello, i'm having problems with my ubuntu 12.04 when i try to update i get this text :
[B]david@david-desktop:~$ sudo apt-get update
E: Type 'b-src' is not known on line 1 in source list /etc/apt/sources.list.d/cheleb-blender-svn-precise.list
E: The list of sources could not be read.[/B]

---

### Post by steeldriver on 2012-07-12
did you look at /etc/apt/sources.list.d/cheleb-blender-svn-precise.list - maybe a 'deb-src' entry got truncated to 'b-src' ?

---

