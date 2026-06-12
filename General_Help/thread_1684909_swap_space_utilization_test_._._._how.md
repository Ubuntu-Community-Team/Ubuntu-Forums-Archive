---
title: "swap space utilization test . . . how ?"
date: 2011-02-09
forum: General Help
---

### Post by jenaniston on 2011-02-09
Is there any decent way to see*** if*** the swap area - or how *much of *the swap area -
is actually being used, especially at bootup . . .
 
. . . maybe something like the "benchmark" tests - but just for swap ??
 
I am testing U9.04 as well as **L**ubuntu 10.10 (and trying **X**ubuntu 10.10 and 11.04alpha2 next)
running on an old and very small RAM (128MB) Gateway tower.
 
I've been making swap partitions using **mkswap** -
which has made running U9.04 even *possible* - no more frozen screens -
but I now wonder if **L**ubuntu needs to be "told" to use the swap area?? (mstab ??)

---

### Post by cipherboy_loc on 2011-02-09
Try:```
free -m
```


Run it at different times to see what happens. You could create an init script to monitor it and save the output of the command to a log file every 5 seconds or so.








Cipherboy

---

