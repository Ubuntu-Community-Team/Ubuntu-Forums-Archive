---
title: "Question about /home"
date: 2009-07-07
forum: General Help
---

### Post by aldrin_0514 on 2009-07-07
hi, i just installed ubuntu 9.04 last night, and i noticed that my /home directory is inside the file system drive, is this normal? or i made a mistake in partitioning?

---

### Post by abhilashm86 on 2009-07-07
which mount option did you select while installing?? is it / or /home, it depends on your mount point.......

---

### Post by Celauran on 2009-07-07
Check with 

```
df -h
```

This will show what's mounted on which partition.

---

### Post by CatKiller on 2009-07-08
Unless you specified anything else, that's normal. Having /home on a separate partition is useful to some people, but it's not necessary for everyone.

---

### Post by 3rdalbum on 2009-07-08
Yes, that's correct: Your /home directory is inside the filesystem.

If you put your /home on a different partition or even a different hard disk, it still gets mounted inside /home on the filesystem. Perfectly normal.

---

