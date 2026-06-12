---
title: "Linux using way too much RAM"
date: 2010-09-11
forum: General Help
---

### Post by Jotapee on 2010-09-11
I use ubuntu 10.04 64bit and my server config is:
Core2Quad Q9400 2.4GHz, 8GB RAM

Ubuntu is using almost 100% of server's RAM and I really don't know why.

When I run "top" command I get this:

```

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
5895 jotape    20   0 3268m 3.1g 6296 S    3 39.3 205:20.07 rwar
   1 root      20   0 23576 1836 1264 S    0  0.0   0:00.94 init
   2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd
   3 root      RT   0     0    0    0 S    0  0.0   0:00.02 migration/0
   4 root      20   0     0    0    0 S    0  0.0   3:30.82 ksoftirqd/0
   5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0
   6 root      RT   0     0    0    0 S    0  0.0   0:00.03 migration/1
   7 root      20   0     0    0    0 S    0  0.0   0:09.07 ksoftirqd/1
   8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1
   9 root      RT   0     0    0    0 S    0  0.0   0:00.01 migration/2
  10 root      20   0     0    0    0 S    0  0.0   5:20.65 ksoftirqd/2
  11 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/2
  12 root      RT   0     0    0    0 S    0  0.0   0:00.07 migration/3
  13 root      20   0     0    0    0 S    0  0.0   0:04.06 ksoftirqd/3
  14 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/3
  15 root      20   0     0    0    0 S    0  0.0   0:00.01 events/0
  16 root      20   0     0    0    0 S    0  0.0   0:00.18 events/1
  17 root      20   0     0    0    0 S    0  0.0   0:37.70 events/2

```But, as you can see, there's nothing consuming this much RAM.

Help ? :p

Thank you

---

### Post by Gunman1982 on 2010-09-11
In default top sorts the processes with the highest cpu utilization first. Hit 'M' (captial m) to sort depending on mem usage.

---

### Post by hrickh on 2010-09-11
> **Jotapee said:**
> 
Ubuntu is using almost 100% of server's RAM and I really don't know why.

How did you determine that Ubuntu is the memory culprit?

If you're coming from a Windows environment, be aware that Linux allocates memory much differently, and seeing all your memory used by the OS (Linux) is not a bad thing.

R.
==

---

### Post by CharlesA on 2010-09-11
Check out what the free command says:

```
free -m
```

---

### Post by hrickh on 2010-09-11
> **CharlesA said:**
> Check out what the free command says:

```
free -m
```
The number you want to look at in that output is the used buffers.

R.
==

---

### Post by WorMzy on 2010-09-11
I'm not sure what this "wrar" process is, but it seems to be used a considerable amount of RAM. What is it?

---

