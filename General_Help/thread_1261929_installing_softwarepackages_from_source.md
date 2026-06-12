---
title: "installing software/packages from source"
date: 2009-09-09
forum: General Help
---

### Post by e24ohm on 2009-09-09
Folks:
I am learning how to install packages from source in my class. My book goes into detail on how to do the following: make, ./install, etc.; however, once you install so many different packages/software what is the easiest way to get a list of installed software and their corrisponding location?

Also, my text book shows examples how to use ./uninstall or make uninstall. Is this common?

thank you
J

---

### Post by CatKiller on 2009-09-09
Personally, I'd recommend the use of *checkinstall* rather than *make install*; it automatically creates and installs a .deb file, so that all your compiled applications are integrated with the package manager, which makes updating or removing them significantly easier.

---

