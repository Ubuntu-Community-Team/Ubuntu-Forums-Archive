---
title: "fdisk + delete partitions + write table. Recoverable?"
date: 2006-03-19
forum: General Help
---

### Post by qqizle on 2006-03-19
A "friend" opened a terminal window, su to root, fdisk, delete all partitions, pressed 'w' to write... now the comp doesn't boot LOL (of course) ... is there anyway to recover the old partitions?

---

### Post by NeghVar on 2006-03-19
Im taking a shot in the dark here but he aint your friend no more is he...

I don't think you can recover it, Your pretty much stuck there.

---

### Post by lha on 2006-03-20
Try [gpart]("http://www.stud.uni-hannover.de/user/76201/gpart/"), it tries to guess what your partition table should look like based on the contents of your hd.

---

