---
title: "Dual Boot going directly to Windows"
date: 2010-03-25
forum: General Help
---

### Post by kooia on 2010-03-25
Hey everyone,

My main operating system is Windows, I just installed Ubuntu because it's super cool, and I like to practice my programming skills on it.  How can I change the GRUB settings so it goes to Windows automatically, not Ubuntu?

---

### Post by pbpersson on 2010-03-25
go to Synaptic and install StartupManager, it will allow you to easily set how GRUB works

---

### Post by johnson.d on 2010-03-26
You can probably install a GUI tool to choose between the defaults in the grub, by using the following command:

$ sudo apt-get-install grub-choose-default

---

