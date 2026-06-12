---
title: "qt"
date: 2006-06-13
forum: General Help
---

### Post by bobaymon on 2006-06-13
I'm trying to install Qt open src 4.1.3; but during "make" it reports that it cannot find -lXrender. I check Synaptic and found that I have libxrender1. Any suggestion?

---

### Post by givré on 2006-06-13
do you have the -dev version of libxrender1 install ?
I can't check if it exist (i'm not at home :cool: ) but most of this type of error is due to a -dev package missing.

---

### Post by dresnu on 2006-06-13
Check out this: [https://wiki.ubuntu.com/CheckInstall?highlight=%28checkinstall%29](https://wiki.ubuntu.com/CheckInstall?highlight=%28checkinstall%29).
Theoretically auto-apt should install all necessary packages.

---

### Post by bobaymon on 2006-06-13
thank you both, libxrender1-dev did the trick

---

