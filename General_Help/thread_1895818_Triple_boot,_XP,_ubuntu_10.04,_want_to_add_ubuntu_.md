---
title: "Triple boot, XP, ubuntu 10.04, want to add ubuntu 11.10"
date: 2011-12-15
forum: General Help
---

### Post by tc101 on 2011-12-15
I have a computer running just fine doing dual boot of win XP and ubuntu 10.04.  I would like to play with ubuntu 11.10 but don't want to let go of 10.04 yet.  How hard is it to set up a triple boot?

---

### Post by seawolf167 on 2011-12-15
Simply resize [some] partition to create more free space for you to install on then install there and run 

```
sudo update-grub
```to find the new installation.

As a side note, don't use the same /home partition between the two since I suspect there will be some [big] issues having 10.04 using Gnome and 11.10 using Unity both accessing the same configuration files at ~/

Backups are always a good idea - I suggest [Clonezilla ]("http://www.clonezilla.org")to make a disk image just in case something happens you can restore it (including the MBR and partition boot loaders) to exactly the same state before you started the new install.

---

