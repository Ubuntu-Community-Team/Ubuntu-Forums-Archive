---
title: "What is /dev directory?"
date: 2010-02-09
forum: General Help
---

### Post by rjwarrier on 2010-02-09
i recently installed Ubuntu 9.10 using Wubi in my dell laptop. In Ubuntu, my home folder shows a free space of arnd 400 MB while the '/dev' folder shows a free space of 1.5 GB. When i checked the free space, it showed the /dev as 'tempfs'.. can i free the space used by this tempfs? whats the purpose of /dev dir?

---

### Post by diesch on 2010-02-09
/dev is a virtual directory, that is it doesn't exist anywhere on your disk. It contains special files (called device files) which work as an interface to the kernel. This files are automatically created and removed by the kernel (more exactly: by udev).

---

### Post by rjwarrier on 2010-02-09
so can i use the space shown as tmpfs? it shows 1.5 GB free in tmpfs while my home dir shows a free space of arnd 400 MB!!

---

### Post by chewearn on 2010-02-09
> **rjwarrier said:**
> so can i use the space shown as tmpfs? it shows 1.5 GB free in tmpfs while my home dir shows a free space of arnd 400 MB!!

No, you can't use the space.  It's a temporarily space and does not exist on hard disk.  If you save data in it, the data will be lost when you shutdown/reboot.

---

### Post by diesch on 2010-02-09
No. /dev only exists in RAM and the free space is not really free space but shows how much it can still grow.

---

### Post by lisati on 2010-02-09
> **rjwarrier said:**
> i recently installed Ubuntu 9.10 using Wubi in my dell laptop. In Ubuntu, my home folder shows a free space of arnd 400 MB while the '/dev' folder shows a free space of 1.5 GB. When i checked the free space, it showed the /dev as 'tempfs'.. can i free the space used by this tempfs? whats the purpose of /dev dir?

You might want to have a look here: [http://www.linux.org/lessons/beginner/l4/lesson4e.html](http://www.linux.org/lessons/beginner/l4/lesson4e.html)

---

### Post by rjwarrier on 2010-02-09
thnx for the replies!!

---

