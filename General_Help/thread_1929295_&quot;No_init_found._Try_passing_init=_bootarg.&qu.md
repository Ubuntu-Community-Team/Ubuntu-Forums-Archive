---
title: "&quot;No init found. Try passing init= bootarg.&quot;"
date: 2012-02-21
forum: General Help
---

### Post by Kitkin15 on 2012-02-21
Ubuntu 10.10 did a random disk check and for some reason it had a problem, now it will not boot the OS Like it should and it comes up with this screen. I dont understand why this is happening and i dont know how to fix it.

Is there a way to fix this? A file thats missing or corrupted that i can exchange with a good one?

  ~Kitkin15

fsck -y /dev/sda1
Replace "sda1" with whatever partition yours is on, make sure you unmount your partition. Use a boot up disk

I fixed it with the above code ^

This is now solved.

---

