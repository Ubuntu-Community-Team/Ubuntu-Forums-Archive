---
title: "Any problem with my mem usage?"
date: 2010-05-15
forum: General Help
---

### Post by vzhen on 2010-05-15
my free -m here.
Mem: used 1838  free 47 what is this?
buffers/cache  used 687  free 1198  what is this?

I just open rhythmbox, chromium, IM, stardict, firefox.


```
vzhen@vzhen-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1885       1838         47          0         87       1063
-/+ buffers/cache:        687       1198
Swap:         3812          1       3811
```

---

### Post by howefield on 2010-05-15
It's the second line you want to look at.

687 megs used, and 1198 free.

---

