---
title: "editing the grub boot manager"
date: 2010-07-05
forum: General Help
---

### Post by reica on 2010-07-05
Hi, I've just installed Ubuntu 10.04.
In previous versions I could edit the grub menu (menu.lst).
Where can I find the menu.lst or it's equivalent in 10.04 ?
Rein

---

### Post by wilee-nilee on 2010-07-06
> **reica said:**
> Hi, I've just installed Ubuntu 10.04.
In previous versions I could edit the grub menu (menu.lst).
Where can I find the menu.lst or it's equivalent in 10.04 ?
Rein

Grub2 is different and can be modified but you may want to state your intentions as it may help others to instruct you to a link...etc

---

### Post by merlinus on 2010-07-06
/boot/grub/grub.cfg is where the settings are kept.  You can change some of these in /etc/default/grub

Here is a guide to grub 2:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by reica on 2010-07-07
> **merlinus said:**
> /boot/grub/grub.cfg is where the settings are kept.  You can change some of these in /etc/default/grub

Here is a guide to grub 2:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Thank you....solved the problem.

---

