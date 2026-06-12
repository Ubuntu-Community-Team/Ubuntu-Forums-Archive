---
title: "Boot Order"
date: 2009-12-07
forum: General Help
---

### Post by conradin on 2009-12-07
Hi All,
This should be a quick question. I just installed Xubuntu 9.10 on a coworkers computer. I think he'll want to boot into Windows xp by default. I went to edit /boot/grub/menu.lst but I don't see it there.
is the menu list called something different? Where can I go to edit the menu list?

---

### Post by Vishnu V on 2009-12-07
the equivalent file in ubuntu 9.10 is /

/boot/grub/grub.cfg

change default "0" to boot position of windows

---

### Post by audiomick on 2009-12-07
9.10 uses grub2 as opposed to the "old" grub up to 9.04
There is a tutorial here, apart from the grub2 page in Ubunut Documentation
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

---

### Post by conradin on 2010-01-08
It worked! Thanks Guys!:D

---

