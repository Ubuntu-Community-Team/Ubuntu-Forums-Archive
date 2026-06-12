---
title: "Can't get grub menu"
date: 2010-07-04
forum: General Help
---

### Post by J V on 2010-07-04
On Lucid lynx, holding shift won't get me the grub menu... Any thoughts?

---

### Post by dino99 on 2010-07-04
you need to hold it down at end of bios process

you can unhide it by changing setting into /etc/default/grub

more info below

---

### Post by J V on 2010-07-04
Ok, the problem is that it's set for timed boot which doesn't have shift enabled, but the timer is set to 0... So how do I change it to hidden boot so I can hold shift and see the menus?

---

### Post by last1home on 2010-07-04
[I]message deleted
[/I]

---

### Post by philinux on 2010-07-04
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by J V on 2010-07-04
Thanks Phil, I've read both of them, but according to link #1, I need to set "**GRUB_HIDDEN_TIMEOUT=0**" - but this won't work for multiple OS', it gives a general link to another thread as to how to get it to work for multi-OS systems but... I have no idea where in there the problem is...

Edit: Found it, thanks

---

