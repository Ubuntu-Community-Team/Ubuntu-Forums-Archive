---
title: "Moving swap location?"
date: 2011-04-28
forum: General Help
---

### Post by wahsape on 2011-04-28
First off, can you move your swap to a new location after a install and if it is possible will it give any kind of performance boost if it is moved to a separate hard drive?

I did this on my XP machine and it made a pretty big difference in over all speed of the machine and wanted to try this on my Ubuntu machine, assuming it will even make and difference in performances.

---

### Post by oldfred on 2011-04-28
I like to keep all system partitions on one drive, so when one drive dies, I can still boot the other. I always put a swap on every drive, but only mount the one on the current system's drive.

You do not want to use swap, it is orders or magnitude slower than memory. Part of Linux's advantage is it uses less memory. How much memory do you have. If only 512MB or less then you may be using swap. Or if editing videos with lots of memory you may get to using swap.

Memory use including swap
free -m

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by wahsape on 2011-04-29
I have 2G of RAM but I run multiple instances of a game at once so it is memory intensive at times.

I moved the swap to its own hard drive on my windows box and it made a noticeable improvement and was wondering if I could do the same with the Ubuntu box.

Here is the output from "free -m" running multiple instances of the game. 

```
            total       used       free     shared    buffers     cached
Mem:          2011       1958         52          0         38        576
-/+ buffers/cache:       1343        667
Swap:         2902         21       2881
```

If I'm reading this correctly it is showing very little swap being used right?

My best solutions would be to add more RAM then?

---

### Post by oldfred on 2011-04-29
If you can add RAM that almost always is the best way to speed up a system. 

Your memory in use is high since Linux keeps last used app/data in case you reuse it and only frees it if you load something new. So memory is always in use.

---

