---
title: "High memory usage"
date: 2011-07-15
forum: General Help
---

### Post by uShafee on 2011-07-15
I find ubuntu crashing on me often recently. I think i am running out of memory.

I ran the free -m command and found that my memory usage was really high. So then, i ran top to find the culprit, but the displayed processes were using less than 1.5% of m. how do i know which program is making ubuntu crash/eating up memory? Below is the output
```

shafee@shafee-pc:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3824       3714        110          0        978       1954
-/+ buffers/cache:        780       3044
Swap:           99          0         99

shafee@shafee-pc:~$ top
top - 02:12:14 up  1:24,  2 users,  load average: 0.16, 0.42, 1.49
Tasks: 182 total,   1 running, 181 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.9%us,  1.9%sy,  0.3%ni, 79.3%id, 15.5%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   3916708k total,  3803848k used,   112860k free,  1002308k buffers
Swap:   102396k total,        0k used,   102396k free,  2001852k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4200 root      20   0  289m  53m  38m S    2  1.4   1:06.45 Xorg               
 5590 shafee    20   0 19348 1368  956 R    2  0.0   0:00.01 top                
    1 root      20   0 24124 2136 1264 S    0  0.1   0:02.05 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:24.23 ksoftirqd/0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    9 root      20   0     0    0    0 S    0  0.0   0:00.11 ksoftirqd/1        
   11 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2        
   13 root      20   0     0    0    0 S    0  0.0   0:03.89 ksoftirqd/2        
   14 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/3        
   16 root      20   0     0    0    0 S    0  0.0   0:00.16 ksoftirqd/3        
   17 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset             
   18 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper            
   19 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns              
   21 root      20   0     0    0    0 S    0  0.0   0:00.01 sync_supers        
shafee@shafee-pc:~$

```

---

### Post by uShafee on 2011-07-15
nm. I was reading the output by **free** wrong and my crashes seems to be related to something else.

---

### Post by dabl on 2011-07-15
I don't think your system has a problem -- it is not swapping and half of the "used" memory is for cache (a _good_ thing).

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

