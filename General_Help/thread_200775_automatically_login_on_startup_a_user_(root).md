---
title: "automatically login on startup a user (root)"
date: 2006-06-20
forum: General Help
---

### Post by odysseus.lost on 2006-06-20
Hi,

this questions has two parts and I am referring to a console only installation, ie no graphical interface... think of either ubuntu server or any ubuntu booting on runlevel 3. So,
1. How do you automatically login a user upon startup?
2. How can this user be root?

Cheers!

---

### Post by glotz on 2006-06-20
Maybe just make the box start with additional kernel parameters **rw init=/bin/bash**. (in /boot/grub/menu.lst)

---

