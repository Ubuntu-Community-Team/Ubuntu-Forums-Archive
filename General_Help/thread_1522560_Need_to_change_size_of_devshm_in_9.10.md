---
title: "Need to change size of /dev/shm in 9.10"
date: 2010-07-02
forum: General Help
---

### Post by melgish on 2010-07-02
I need to know how to change the default size of /dev/shm on a 9.10 box.

In previous versions this was controlled by the value in /etc/defaults/tmpfs but this no longer works.

What is the correct method to change the default size?

---

### Post by dino99 on 2010-07-02
ive found this:

[http://www.cyberciti.biz/tips/what-is-devshm-and-its-practical-usage.html](http://www.cyberciti.biz/tips/what-is-devshm-and-its-practical-usage.html)

---

### Post by melgish on 2010-07-02
Yes, I found that page too but the choices there involve remounting /dev/shm after the fact, or creating a different tmpfs altogether.

Neither addresses the real issue which is 9.10 and later broke the long established way to set the default size and nobody seems to know the right way to fix it.

---

