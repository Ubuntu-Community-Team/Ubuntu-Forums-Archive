---
title: "Can't start a system"
date: 2010-01-09
forum: General Help
---

### Post by santik-solnce on 2010-01-09
I've upgrade  jaunty jackalope to karmic koala. First of all I've found that firefox doesn't work correctly: it was impossible to open any page. Than desktop became black without signs and I restarted system. But it was unsuccessfully, I saw this:

[http://s006.radikal.ru/i215/1001/dc/82e343445d86.jpg](http://s006.radikal.ru/i215/1001/dc/82e343445d86.jpg)

than:

[http://s41.radikal.ru/i091/1001/08/949350a5d38e.jpg](http://s41.radikal.ru/i091/1001/08/949350a5d38e.jpg)

and after "ctrl+d":

[http://s54.radikal.ru/i146/1001/fc/d4b84df4e27b.jpg](http://s54.radikal.ru/i146/1001/fc/d4b84df4e27b.jpg)

Please, help me. What should I do?

---

### Post by marco123 on 2010-01-09
Manually check the filesystem: 

> fsck /dev/sda1

then see if it boots.

---

### Post by santik-solnce on 2010-01-09
Now I have this:

[http://i067.radikal.ru/1001/a6/4bfe309bef0b.jpg](http://i067.radikal.ru/1001/a6/4bfe309bef0b.jpg)

---

### Post by happyhamster on 2010-01-09
Choose y (yes), to let fsck fix the error. Note that there could be (many) more errors after this one.

---

### Post by santik-solnce on 2010-01-09
after "y"

> Inode 958638 was part of the orphaned inod list. FIXED.
Inode 958640 was part of the orphaned inod list. FIXED.



---

### Post by happyhamster on 2010-01-09
That means fsck found some stuff (files/folders) it doesn't know where to put. They will be put in the lost+found folder in /home. You should take a look in that folder later, when all checks have completed.

BTW, make sure fsck finishes its check completely, don't abort somewhere in the middle.

---

### Post by santik-solnce on 2010-01-09
Thanks a lot! It works.
But I have a problem with firefox - it can't open any page, but the internet connection is ok.
Also there are problems with visual effects: if effects are in standart mode, the desktop becomes black without signs, if we choose mode with no effects, it's ok.

---

