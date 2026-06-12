---
title: "Xorg eating up a lot of RAM"
date: 2010-02-18
forum: General Help
---

### Post by yang on 2010-02-18
Xorg is eating up 444MB of 2GB total RAM on my Ubuntu 9.10 x86_64 machine with nvidia drivers installed for the nvidia G86 (GeForce 8300 GS). top shows:

```

top - 18:21:41 up 6 days,  2:40,  9 users,  load average: 0.46, 1.12, 1.22
Tasks: 266 total,   3 running, 262 sleeping,   1 stopped,   0 zombie
Cpu(s):  8.4%us,  2.0%sy,  0.0%ni, 89.1%id,  0.5%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2055736k total,  1965136k used,    90600k free,     3952k buffers
Swap:   979924k total,   979908k used,       16k free,   102636k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                                                                        
 1432 root      20   0 1154m 442m 7492 S    8 22.0  32:56.97 Xorg                                                                                                                                                                            
18462 yang      20   0 1001m 219m 8356 S    0 10.9   5:13.25 chrome                                                                                                                                                                          
24099 yang      20   0  865m  83m  13m S    0  4.2   0:06.91 chrome                                                                                                                                                                          

```

xrestop shows:

```

xrestop - Display: :0.0
          Monitoring 47 clients. XErrors: 0
          Pixmaps:   40430K total, Other:     142K total, All:   40573K total

res-base Wins  GCs Fnts Pxms Misc   Pxm mem  Other   Total   PID Identifier    
1c00000    21   46    1   19  697     9128K     18K   9146K  3169 x-nautilus-desktop
1000000     4    3    0   17  194     9000K      4K   9004K  3134 gnome-settings-daemon
1600000    51    2    1   25 1100     7648K     28K   7676K   ?   compiz

```

For comparison, here's my other Ubuntu box, which also has compiz etc. enabled but with ATI RV370 (Radeon X300SE):

```

top - 18:18:18 up 58 days,  4:27,  9 users,  load average: 0.00, 0.00, 0.00
Tasks: 224 total,   1 running, 223 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.3%us,  0.3%sy,  0.0%ni, 98.8%id,  0.5%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1024964k total,   987124k used,    37840k free,   247012k buffers
Swap:  2048276k total,    94296k used,  1953980k free,   264744k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                                                                        
24324 yang      20   0 61936  35m 6364 S    0  3.5   4:35.84 nxagent                                                                                                                                                                         
 1768 ntop      20   0  190m  32m 5388 S    1  3.2 283:36.15 ntop                                                                                                                                                                            
 1178 root      20   0 60588  29m 1788 S    0  3.0   5:48.89 console-kit-dae                                                                                                                                                                 
...
 1315 root      20   0  343m 4956 4020 S    0  0.5   3:43.87 Xorg                                                                                                                                                                            

```

Any ideas on how to get to the bottom of this? (i.e. not "Log out"/"Reboot") Thanks in advance.

---

### Post by Pjotr123 on 2010-02-18
Disable the visual effects:
[http://sites.google.com/site/easylinuxtipsproject/tips#TOC-Make-your-system-faster-and-quieter](http://sites.google.com/site/easylinuxtipsproject/tips#TOC-Make-your-system-faster-and-quieter)

---

### Post by yang on 2010-02-18
The memory consumption is anomalous even for systems with visual effects enabled (read further down my post).

---

### Post by yang on 2010-03-02
Anyone? Xorg doesn't gobble up memory right off the bat... I was using the system for several days without issue when the consumption suddenly surged up again just now.

---

