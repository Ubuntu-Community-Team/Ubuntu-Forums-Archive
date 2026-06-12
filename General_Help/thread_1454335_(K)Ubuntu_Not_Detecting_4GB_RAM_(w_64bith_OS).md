---
title: "(K)Ubuntu Not Detecting 4GB RAM (w/ 64bith OS)"
date: 2010-04-14
forum: General Help
---

### Post by zzzBrett on 2010-04-14
I'm running Kubuntu 9.10 x64 and have 4GB RAM (as detected by my bios). However, when i run free -m, it reports:

```
             total       used       free     shared    buffers     cached
Mem:          3271        915       2355          0         69        333
-/+ buffers/cache:        512       2758
Swap:         7812          0       7812
```

Anyone know why this is happening?

---

### Post by darolu on 2010-04-14
What kind of video card do you have? if it's integrated, is most likely taking Video-RAM from your main RAM.

Keep in mind that the kernel keeps some RAM for it (so it is stable), it eats ~40MB in my system.
```
~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3962        948       3013          0         71        326
-/+ buffers/cache:        550       3412
Swap:         1427          0       1427
```

---

### Post by zzzBrett on 2010-04-14
I should have 4GB RAM, so i'm missing about .75 GB -- probably too much for the kernel. My video is not integrated. Any other ideas?

---

### Post by darolu on 2010-04-14
What do you get with:
```
$ uname -a
```

---

### Post by zzzBrett on 2010-04-14
```
Linux computer 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux

```

---

### Post by zzzBrett on 2010-04-15
Any ideas?

---

### Post by zzzBrett on 2010-04-19
Just installed Ubuntu 10.04 beta 2 -- same problem.
..bump

---

### Post by zzzBrett on 2010-04-21
bump

---

