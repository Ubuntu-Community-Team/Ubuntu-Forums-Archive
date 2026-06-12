---
title: "Mysterious Memory Leak"
date: 2012-08-07
forum: General Help
---

### Post by dev.null on 2012-08-07
Lenovo w530. 32G ram (and it's a good thing)

Ubuntu 12.04 installed via alternate.

I've had this laptop for less than a week. Overall nice. But I've got this weird condition where more and more memory is being used, but using top doesn't show who the culprit is. It's almost as if the kernel loses the memory.

Little by little over time the total memory used increases without any application claiming it, restarting X doesn't bring it back, the only way to get the memory back is by reboot.

Here's a snapshot of top where 23G is taken, and the apps are sorted by memory usage, and there's no way it adds up to 23G:

```
top - 23:23:53 up 1 day,  3:26,  1 user,  load average: 0.39, 0.62, 0.83
Tasks: 206 total,   2 running, 202 sleeping,   0 stopped,   2 zombie
Cpu0  :  0.0%us,  0.3%sy,  0.0%ni, 98.0%id,  1.7%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu1  :  0.0%us, 10.6%sy,  0.0%ni, 89.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu2  :  0.3%us,  1.0%sy,  0.0%ni, 98.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu3  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu4  :  0.0%us,  0.3%sy,  0.0%ni, 99.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu5  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu6  :  2.0%us,  1.0%sy,  0.0%ni, 97.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu7  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:  32538348k total, 23737256k used,  8801092k free,   209720k buffers
Swap: 31250428k total,        0k used, 31250428k free, 21722108k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                  
11074 root      20   0 4088m 3680 2676 S    0  0.0   0:00.01 /usr/sbin/console-kit-daemon --no-daemon                 
 2147 rpickett  20   0 1019m  52m  24m S    0  0.2   0:07.28 nautilus -n                                              
 3887 rpickett  20   0  960m  71m  30m S    0  0.2   7:09.10 uex                                                      
11044 rpickett  20   0  881m  79m  18m S    0  0.3   0:04.32 /usr/lib/chromium-browser/chromium-browser --type=rendere
 3542 rpickett  20   0  865m  60m  34m S    0  0.2   1:14.15 cairo-dock                                               
10963 rpickett  20   0  838m  33m  14m S    0  0.1   0:00.48 /usr/lib/chromium-browser/chromium-browser --type=rendere
10954 rpickett  20   0  830m  28m  14m S    0  0.1   0:00.25 /usr/lib/chromium-browser/chromium-browser --type=rendere
10980 rpickett  20   0  829m  27m  13m S    0  0.1   0:00.32 /usr/lib/chromium-browser/chromium-browser --type=rendere
10972 rpickett  20   0  828m  25m  12m S    0  0.1   0:00.17 /usr/lib/chromium-browser/chromium-browser --type=rendere
11020 rpickett  20   0  828m  23m  11m S    0  0.1   0:00.13 /usr/lib/chromium-browser/chromium-browser --type=rendere
10995 rpickett  20   0  827m  25m  13m S    0  0.1   0:00.15 /usr/lib/chromium-browser/chromium-browser --type=rendere
10987 rpickett  20   0  827m  23m  12m S    0  0.1   0:00.14 /usr/lib/chromium-browser/chromium-browser --type=rendere
11009 rpickett  20   0  827m  22m  11m S    0  0.1   0:00.12 /usr/lib/chromium-browser/chromium-browser --type=rendere
11068 rpickett  20   0  732m  19m  14m S    0  0.1   0:00.18 /usr/lib/gnome-settings-daemon/gnome-settings-daemon     
```

Ideas on what I should start digging into?

---

### Post by Statia on 2012-08-07
You are aware of how Linux manages memory?

[http://www.linuxhowtos.org/System/Linux%20Memory%20Management.htm](http://www.linuxhowtos.org/System/Linux%20Memory%20Management.htm)

---

### Post by jwbrase on 2012-08-07
Well, about 21 GiB of that 23 GiB is accounted for by the "cached" entry. Basically, if nothing else is using up memory, the kernel uses as much memory as it can to provide fast access to commonly used files (because reading from disk is much slower than from RAM). But the kernel will kick files out of cache if it needs it for programs, so as far as the user is concerned, the cache is free memory. Free + buffers + cached + free swap is what's available to programs.

So it's nothing to worry about.

---

