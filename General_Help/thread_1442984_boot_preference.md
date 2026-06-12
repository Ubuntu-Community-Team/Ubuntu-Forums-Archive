---
title: "boot preference"
date: 2010-03-30
forum: General Help
---

### Post by pickupman on 2010-03-30
hello
i just built a new system and have windows xp on it, i also installed ubuntu to play around with, i want windows to be the defualt boot instead of ubuntu, so i found the instructions on the net, but my problem is when i type sudo gedit /boot/grub/menu.lst    i  dont c a darn word or nothin, how do i get to be able to see something so i can edit the darn thing and get it to start to windows...my fiance doesn't really like to go to linux

---

### Post by zvacet on 2010-03-30
From synaptic install start up manager and with it select witch OS will be your default.

---

### Post by ajgreeny on 2010-03-30
Yes, you can use startup manager for that, but not much else at the moment.

The reason you have an empty, or non-existent **menu.lst** is because you probably have installed ubuntu 9.10, which has moved to grub2.  This works quite differently from legacy grub, and has a read-only **grub.cfg** file to replace menu.lst.  grub.cfg can not be edited manually, (actually it can, but it's pointless as it will revert when you run update-grub) and is edited by a number of shell scripts which are themselves run by the **update-grub** command.

have a look at [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

