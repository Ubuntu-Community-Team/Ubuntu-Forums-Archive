---
title: "Interpreting /proc/cpuinfo flags"
date: 2010-11-08
forum: General Help
---

### Post by stair314 on 2010-11-08
Is there any resource for figuring out what the flags listed by /proc/cpuinfo mean? I've seen people on other sites point to a file called cpufeatures.h but it seems to be very incomplete.

In particular, I have two different Core i7 machines and the one with the lower clock rate is actually running faster on benchmark tests. I'm trying to find out why. I think it is partly due to better memory bandwidth on the machine with lower clock rate, but the one with higher clock rate is also losing to a third machine with a Core 2 Quad and much lower memory bandwidth.

They two Core i7 machines very different cpuinfo flags and I think this may be related to why the one is running slow:

flags that are unique to the Core i7 machine with lower clock rate:
nopl

flags that are unique to the Core i7 machine with higher clock rate but poor performance:
xtopology
nonstop_tsc
aperfmperf
dtes64
pdcm
tpr_shadow
vnmi
flexpriority
ept
vpid

If anyone can tell me how to figure out what these flags mean, it would be very helpful.

---

