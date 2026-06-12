---
title: "GRUB and Windows 7 RC1"
date: 2009-10-28
forum: General Help
---

### Post by Eragon0605 on 2009-10-28
When I attempt to load the "Windows Vista (loader)", GRUB just decides to reset. I edited the options in menu.lst, but I can't figure out what to change. Under the windows section, it says

title        Windows 7
rootnoverify    (hd0,0)
savedefault
chainloader    +1

What do I change to make this work? (Oh, and I changed the name from "Windows Vista (loader)" to "Windows 7")

EDIT: Oh, and I have Ubuntu 9.10, so I got whatever version of GRUB that comes with 9.10.

---

### Post by Eragon0605 on 2009-10-29
Helooooo... Anyone? Oh, and do you think that maybe the Win7 bootmgr was overwritten? If so, How do I re-install all that crap, short of re-installing windows.

---

