---
title: "High load while idle"
date: 2011-01-14
forum: General Help
---

### Post by [mm] on 2011-01-14
Hi, I have the phenomenon that I sometimes get a very high load on my machine but I don't know where it comes from:

```
top - 11:39:12 up 294 days, 19:34,  1 user,  load average: 14.60, 5.69, 4.13
Tasks: 215 total,   1 running, 214 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.0%us,  0.4%sy,  0.1%ni, 97.0%id,  0.4%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8194004k total,  7905080k used,   288924k free,   197220k buffers
Swap:  4200888k total,      768k used,  4200120k free,  4960292k cached
```

I have a quad core CPU so everything above 4 should be too high but it is doing nothing, there is no waiting for IO or swapping.

Could anyone tell me how exactly the load is calculated and which of the factors is missing from tools like top oder htop?

---

### Post by Brandon Williams on 2011-01-15
The load numbers indicate the average number of processes in the run queue, waiting to get CPU time. A high average means that there are typically a high number of processes in that state.. In some cases, the average could be pushed up really high due to a short lived spike and you won't notice that it happened unless you're paying close attention. Those numbers, even when they're high, don't necessarily indicate a problem, and the fact that you aren't noticing performance degradation means that this is most likely true. Unless you're seeing indications of CPU or I/O bound processes, the load average numbers are nothing to be concerned about.

---

### Post by no2498 on 2011-01-15
install htop
you can kill what ever is running the cpu or memory high

---

### Post by ZebaSz on 2011-01-15
As far as I can see, there's not much load on that PC (97% idle CPU). However, I do see a lot of RAM in use.
If you run "free", you'll see whether the memory is actually in use, or just cached (and reporting as used).

---

### Post by ZebaSz on 2011-01-15
As far as I can see, there's not much load on that PC (97% idle CPU). However, I do see a lot of RAM in use.
If you run "free", you'll see whether the memory is actually in use, or just cached (and reporting as used).

---

