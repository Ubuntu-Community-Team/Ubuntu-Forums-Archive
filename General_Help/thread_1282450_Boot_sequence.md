---
title: "Boot sequence"
date: 2009-10-04
forum: General Help
---

### Post by ianclancy on 2009-10-04
Having installed Ubunto the boot sdequnce defaults to load ubunto. I want to change the load sequence to load Xp as default. What file do I need to modify?

---

### Post by Vaphell on 2009-10-04
/boot/grub/menu.lst
in terminal put **gksu gedit /boot/grub/menu.lst** to launch editor with write permission

you need to find **default 0** and replace 0 with xp position (remember that indexing starts from 0, so if xp is 5th on list you need to put 4 there)

---

### Post by egalvan on 2009-10-04
You can modify the menu.lst as detailed in the above post,
or install StartUpManager with Synaptic or Add/Remove.

This will end up in System/Administration menu as 

Startup-Manager

It is a GUI interfacer to a godly amount of start-up options.

One of them is "Default operating system" under the "Boot" tab.

---

