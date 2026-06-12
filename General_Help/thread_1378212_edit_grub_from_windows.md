---
title: "edit grub from windows"
date: 2010-01-11
forum: General Help
---

### Post by weky on 2010-01-11
I have old computer running ubuntu-server.

I want install windows XP and make dual boot on that machine...

Problem starts when I edit grub file menu.lst and set win XP on first place in the boot menu. 
I can boot into XP but I can't edit menu.lst from XP to set ubuntu on first place in boot menu.

Is there any utility to edit menu.lst from windows?

P.S.
I am connecting to that machine with ssh and rdp because machine running without monitor and keyboard.

Sorry my English is bad...

---

### Post by anaconda on 2010-01-11
if your /boot -folder is in ext3 partition, then you can mount and edit it from windows  
using the fs-driver
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

