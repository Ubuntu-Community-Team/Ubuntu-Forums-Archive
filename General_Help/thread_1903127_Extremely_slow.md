---
title: "Extremely slow"
date: 2012-01-01
forum: General Help
---

### Post by Subbeh on 2012-01-01
Hi,

I'm using Ubuntu 11.04 (PAE-kernel) on my Asus 1215n netbook which has always worked great. Recently I started having performance problems. After about 10 minutes of using Ubuntu, the system gets extremely slow. I don't see anything shocking in CPU or Mem usage. I killed all non-system related processes and changed the swappiness to 0 which didn't help.
I tried a live version from USB which worked just fine, my dual-boot Windows 7 installation works fine as well.

I have no clue what the problem could be... Any help here is appreciated.

---

### Post by TeoBigusGeekus on 2012-01-01
How did you check cpu and ram usage?

---

### Post by Haneef Mubarak on 2012-01-01
Could you try posting your specs and then we might be able to help you better?

ie:

Pentium 4 3.06 GHz HT
4 GB DDR1 RAM


Ubuntu 11.10 w/ Linux PAE


Thanks.

---

### Post by Subbeh on 2012-01-01
I run Ubuntu 11.04 PAE on an Asus 1215n:

Intel Atom D525 (Dual Core; 1.8GHz)
2x2GB DDR3 RAM

This is the output of 'top':

Right after booting when system is stable:
```
top - 00:05:52 up 1 min,  2 users,  load average: 2.36, 0.99, 0.36
Tasks: 164 total,   1 running, 162 sleeping,   0 stopped,   1 zombie
Cpu(s):  0.4%us,  0.6%sy,  0.0%ni, 98.9%id,  0.1%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4104108k total,   639344k used,  3464764k free,    79204k buffers
Swap:  1951740k total,        0k used,  1951740k free,   293612k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                    
  976 root      20   0 48988  13m 7948 S    2  0.3   0:03.60 Xorg                                                                                                       
 1798 steven    20   0  113m  26m  15m S    2  0.7   0:02.00 /usr/bin/termin                                                                                            
   16 root      20   0     0    0    0 S    0  0.0   0:00.06 ksoftirqd/3                                                                                                
 1470 steven    20   0 69080  24m  11m S    0  0.6   0:01.31 gm-notify                                                                                                  
 1876 steven    20   0 72612  29m 9936 S    0  0.7   0:04.09 ubuntuone-syncd                                                                                            
 1897 steven    20   0  2632 1172  864 R    0  0.0   0:00.11 top      
```


This is when the system gets unstable:
```
top - 00:20:58 up 16 min,  2 users,  load average: 1.36, 1.30, 0.81
Tasks: 166 total,   1 running, 164 sleeping,   0 stopped,   1 zombie
Cpu(s):  1.8%us,  1.6%sy,  0.0%ni, 96.4%id,  0.2%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4104108k total,  1286816k used,  2817292k free,   335308k buffers
Swap:  1951740k total,        0k used,  1951740k free,   537836k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                    
  976 root      20   0 78968  18m 9496 S    4  0.5   4:24.29 Xorg                                                                                                       
 2234 steven    20   0  153m  25m  15m S    4  0.6   0:04.58 chromium-browse                                                                                            
 1798 steven    20   0  113m  26m  15m S    2  0.7   0:09.36 /usr/bin/termin                                                                                            
 2250 steven    20   0  2632 1164  864 R    2  0.0   0:00.77 top                                                                                                        
 1447 steven    20   0 78468  12m 9920 S    1  0.3   0:06.51 metacity                                                                                                   
 2222 steven    20   0  188m  69m  20m S    1  1.7   0:46.64 chromium-browse     

```

Let me know if you need more information

---

### Post by Subbeh on 2012-01-02
I just noticed that my CPU gets up to temperature of 92C. In Windows this stays stable at around 60C. Is there a way to control this in Ubuntu?

---

### Post by TeoBigusGeekus on 2012-01-02
Something is terribly wrong with your system, though it can't be seen by top's output.
Try switching to xubuntu or, even better, lubuntu.

---

