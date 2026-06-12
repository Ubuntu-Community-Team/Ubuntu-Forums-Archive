---
title: "gnome-session and gnome-power-manager eat a lot of CPU?"
date: 2010-09-06
forum: General Help
---

### Post by supremedalek on 2010-09-06
I am finding that my 10.04LTS laptop (latest upgrades as of yesterday) is running quite hot (79F). Checking top,

```
top - 07:26:11 up 3 min,  2 users,  load average: 5.56, 2.47, 0.94
Tasks: 275 total,   4 running, 271 sleeping,   0 stopped,   0 zombie
Cpu(s): 74.1%us, 24.3%sy,  0.0%ni,  0.0%id,  0.0%wa,  1.2%hi,  0.5%si,  0.0%st
Mem:   4025408k total,  1245056k used,  2780352k free,   127876k buffers
Swap:  8385920k total,        0k used,  8385920k free,   343396k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
13231 raub      20   0  205m  47m 5884 R   48  1.2   0:28.41 gnome-session      
13532 raub      20   0  249m  87m 6596 R   45  2.2   0:32.97 gnome-power-man    
 2514 root      20   0 53716 3248 2488 S   22  0.1   0:25.74 upowerd            
  990 messageb  20   0 25288 2572  776 S   19  0.1   0:23.64 dbus-daemon        
   23 root      20   0     0    0    0 S    7  0.0   0:10.37 kacpid             
13580 haldaemo  20   0 47060 5304 3924 S    6  0.1   0:11.89 hald               
  457 root      18  -2 17096  988  356 S    4  0.0   0:04.76 udevd              
  452 root      20   0 17036  956  644 S    4  0.0   0:07.50 upstart-udev-br    
  454 root      16  -4 17476 1220  324 S    4  0.0   0:07.17 udevd              
  456 root      18  -2 17096  988  356 S    3  0.0   0:07.49 udevd              
 1166 root      20   0  139m  25m  10m S    3  0.6   0:08.61 Xorg               
    1 root      20   0 23844 2032 1288 S    3  0.1   0:09.79 init               
   24 root      20   0     0    0    0 S    2  0.0   0:09.89 kacpi_notify       
13327 raub      20   0 24080 1636  668 S    2  0.0   0:01.60 dbus-daemon        
13533 raub      20   0  228m  26m  14m S    1  0.7   0:01.08 python             
13534 raub      20   0  359m  22m  15m S    0  0.6   0:01.63 gnome-panel        
13542 raub      20   0  313m  36m 8736 S    0  0.9   0:01.23 compiz 
```

for some reason, gnome-session and gnome-power-manager are eating a lot of of my CPUs, with upowerd being a rather distant third. I do not remember those two programs being so CPU hungry, so what could be causing that? FYI, I have not changed their configurations since I originally installed 10.04 in this machine, a few months ago. Back then the biggest cpu hog was Firefox, with gnome-session and gnome-power-manager being much more efficient in their cpu usage.

---

