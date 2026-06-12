---
title: "High load with low CPU, I/O, Mem"
date: 2011-04-30
forum: General Help
---

### Post by Mekzholan on 2011-04-30
Hi,

I've got a Dell Vostro 3700 laptop that I run Kubuntu 64 bit on. The versions used were 10.10 and now 11.04.

Since the beginning that system has the "problem" that it's allways showing a load of slightly above 1.0 although it's not used, no processes are using the CPU, memory is free and no I/O is beeing done.

Top might look like
```

top - 14:10:35 up  1:36,  2 users,  load average: 1.06, 1.07, 1.05
Tasks: 161 total,   2 running, 159 sleeping,   0 stopped,   0 zombie
Cpu0  :  0.3%us,  0.3%sy,  0.0%ni, 99.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu1  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu2  :  2.7%us,  0.7%sy,  0.0%ni, 96.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu3  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3853268k total,  1856056k used,  1997212k free,    87916k buffers
Swap: 11287548k total,        0k used, 11287548k free,   815152k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                            
 1753 schnecke  20   0  919m 295m  37m S    3  7.8   4:56.63 firefox-bin                        
 1579 schnecke  20   0  731m  39m  25m S    2  1.1   1:39.94 knotify4                           
  930 root      20   0  211m  38m  15m S    0  1.0   1:16.39 Xorg                               
 3114 schnecke  20   0 19352 1348  964 R    0  0.0   0:02.79 top                                
 3347 root      20   0     0    0    0 S    0  0.0   0:00.01 kworker/u:0                        
    1 root      20   0 24148 2268 1360 S    0  0.1   0:01.40 init                               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                           
    3 root      20   0     0    0    0 S    0  0.0   0:00.14 ksoftirqd/0                        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                        
    9 root      20   0     0    0    0 S    0  0.0   0:00.03 ksoftirqd/1                        
   11 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2                        
   13 root      20   0     0    0    0 S    0  0.0   0:00.09 ksoftirqd/2                        
   14 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/3                        
   16 root      20   0     0    0    0 S    0  0.0   0:00.26 ksoftirqd/3                        
[...]

```How can I figure out what's holding the load high?

The real problem with that system is, that the systems sometimes feels quite slow - and very often the fan goes crazy (constantly speeding up and down)

That behaviour was under 10.10 exactly the same!

If it matters: this system has a Core i5 (i.e. integrated graphics) and an nVidia chip. To be able to use it, I blacklisted the nvidia drivers and am running on the Intel chip alone.

---

### Post by Mekzholan on 2011-05-03
Hm, has noone any suggestions?

---

