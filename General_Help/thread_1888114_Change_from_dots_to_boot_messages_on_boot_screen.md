---
title: "Change from dots to boot messages on boot screen"
date: 2011-11-28
forum: General Help
---

### Post by P.ap G on 2011-11-28
Ubuntu 10.04

Changing 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to    GRUB_CMDLINE_LINUX_DEFAULT=

in  /etc/default/grub (working as sudo or sudo su)

then running   sudo  update-grub
 works fine .

The problem arises when doing the same with the LIVE VERSION with persistence.

Anyone got an idea how to solve this please ?

---

