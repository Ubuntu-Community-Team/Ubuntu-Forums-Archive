---
title: "how to multiple extract 40 compressed files and rearrange them"
date: 2011-01-09
forum: General Help
---

### Post by hihihi100 on 2011-01-09
Hi there:

What I want to know is if there is any way I can extract the contents of 40 tgz compressed files without having to open each one of the 40.

The second part of my question, to re arrange the extracted files, is explained now:

THe tree structure of each of these 40 files is:


e000s10:
- Airports
- Objects
- Terrain

e000s20:
- Airports
- Objects
- Terrain

up to 40, while what I need the structure to be is:

Airports (inside this directory, all the 40 files inside each of the 40 extracted files named airports
Objects (inside this one, all the objects folders from the 40 extracted files)
Terrain: as above
 
so the upper level of e000210... disappear

---

### Post by dino99 on 2011-01-09
you might write some bash script

[https://help.ubuntu.com/community/Beginners/BashScripting](https://help.ubuntu.com/community/Beginners/BashScripting)

---

