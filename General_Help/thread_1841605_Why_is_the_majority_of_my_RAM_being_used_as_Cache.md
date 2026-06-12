---
title: "Why is the majority of my RAM being used as Cache?"
date: 2011-09-09
forum: General Help
---

### Post by airspoon on 2011-09-09
Lately, my Ubuntu 11.04 machine is acting kind of strange. For one, my system load seems to be running kind of high. In addition, for some reason the majority of my memory is in use as "cache", as opposed to being "free".

A week or two ago, I had rebooted my system and ran into a huge problem -as Ubuntu wouldn't start back up. However, I was able to get it to start by booting up into a previous kernel.  Then, I rebooted several days later back into the most up to date kernel and *wahlah, it seemed to work again. I have no idea what happened, or what went wrong before.

However, now I'm noticing my load averages being kind of high. I attributed this to a netgear usb 802.11 wireless adapter that was plugged in. So, I unplugged it, connected my machine through Ethernet (on a WDS wireless network, where Ethernet is coming directly from access point, instead of router) and now my load averages seemed to go down -I guess. At least, they are lower than what they were before.

What really is bothering me though and what I believe to be related to the load averages and the prior problem with not booting into Ubuntu, is my memory usage. For instance, right now I have 16% in use by programs and 77% in use as cache. I don't remember it ever using memory like that before.

I'm not sure if this helps or not, but I'll go ahead and list the results of 'top' and 'free -m'.

Here are the results of top:
```

~$ top

top - 17:15:20 up 33 min,  2 users,  load average: 0.22, 0.61, 0.63
Tasks: 165 total,   1 running, 163 sleeping,   0 stopped,   1 zombie
Cpu(s):  2.0%us,  1.0%sy,  0.0%ni, 96.7%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   2318612k total,  2254872k used,    63740k free,    34548k buffers
Swap:  1045500k total,        0k used,  1045500k free,  1789720k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1948 mhartman  20   0  164m  50m  13m S    2  2.2   8:19.93 ubuntuone-syncd    
 2684 mhartman  20   0 62572  14m  10m S    2  0.6   0:00.48 gnome-terminal     
 1041 root      20   0 92172  49m  12m S    2  2.2   0:32.50 Xorg               
 2598 mhartman  20   0  147m  38m  24m S    1  1.7   0:34.57 chromium-browse    
 1845 mhartman  20   0 49100  11m 8776 S    1  0.5   0:12.23 multiload-apple    
 2341 mhartman  20   0  317m  92m  31m S    1  4.1   0:30.77 chromium-browse    
 1713 mhartman  20   0 43804  13m 9836 S    0  0.6   0:01.07 notify-osd         
 2778 mhartman  20   0  2632 1140  848 R    0  0.0   0:00.02 top                
    1 root      20   0  3048 1784 1192 S    0  0.1   0:01.06 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:00.14 ksoftirqd/0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    8 root      20   0     0    0    0 S    0  0.0   0:00.11 kworker/1:0        
    9 root      20   0     0    0    0 S    0  0.0   0:00.11 ksoftirqd/1        

```

And here are the results of free -m:

```

~$ free -m
      total       used       free     shared    buffers  cached                      
Mem:  2264       2199         64          0         33    1744


-/+ buffers/cache:        421       1842
Swap:         1020          0       1020

```

Any idea as to what's going on? Any and all help would be greatly appreciated. I'm an Ubuntu novice. Thanks.

---

### Post by WorMzy on 2011-09-09
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by LowSky on 2011-09-09
Linux caches like crazy. Not an issue, in fact it speeds up your system.
Any issues you may be having could be the result of poor wireless driver support. High load averages could be caused by system processes running amok. Ubuntu-One has been known to cause slowdowns if it is trying to sync large files.

Here are my system stats, as you can see we are operating very similar

```
 ~]$ top

top - 17:32:06 up 1 day,  5:28,  2 users,  load average: 0.00, 0.01, 0.05
Tasks: 172 total,   1 running, 170 sleeping,   0 stopped,   1 zombie
Cpu(s):  0.1%us,  0.2%sy,  0.0%ni, 99.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:  12333396k total, 11929440k used,   403956k free,   213792k buffers
Swap:  4393980k total,       20k used,  4393960k free, 10085180k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 8534 john      20   0 1000m 296m  49m S    1  2.5  11:33.66 mythfrontend       
 1690 root      20   0  220m 120m  12m S    0  1.0   6:55.37 Xorg               
 2021 john      20   0  602m  17m 9252 S    0  0.1   0:03.19 gnome-settings-    
13652 john      20   0  371m  17m  11m S    0  0.1   0:00.27 gnome-terminal     
    1 root      20   0  3916  620  528 S    0  0.0   0:00.94 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:00.04 ksoftirqd/0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.16 watchdog/0         
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
   10 root      20   0     0    0    0 S    0  0.0   0:00.05 ksoftirqd/1        
   12 root      RT   0     0    0    0 S    0  0.0   0:00.16 watchdog/1         
   13 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2        
   15 root      20   0     0    0    0 S    0  0.0   0:00.05 ksoftirqd/2        
   16 root      RT   0     0    0    0 S    0  0.0   0:00.15 watchdog/2         
   17 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/3        
   19 root      20   0     0    0    0 S    0  0.0   0:01.45 ksoftirqd/3  
```
As you can see my memory is being utilized the same way.
```
~]$ free -m
             total       used       free     shared    buffers     cached
Mem:         12044      11657        387          0        208       9849
-/+ buffers/cache:       1599      10445
Swap:         4290          0       4290

```

---

### Post by airspoon on 2011-09-09
Whewww! That's good to know. I was starting to get a little worried. Thanks to both of you. 

worMzy, that webpage is perfect and if I had only seen that prior! It's almost as if it was directly answering my question.

LowSky, thanks for the easily understandable explanation. I was looking at the Ubuntu One and actually thinking that was a problem, I guess it is. I actually tried to turn it off earlier today, though to no avail -as it still seems to be trying to sync my files.

On a different note, is my swap space too low? Should I increase my swap? It is less than half of my RAM and I see that yours is much higher than your RAM. Did I read somewhere that your swap should be two times the installed memory, or is that completely wrong? Thanks again!

---

### Post by jwbrase on 2011-09-09
From the point of view of programs, cache is free memory. If a program requests more memory from the operating system and no empty memory is available, the system takes a chunk of cache memory and gives it to the program. Cache does stuff like mirroring files on disk so that they can be accessed faster. It's not something that has to be there, so if something else needs the memory, the OS reduces the amount of space it uses for caching and gives the memory to whatever needs it.

---

### Post by lisati on 2011-09-09
As far as I know, the tech term "cache" comes from a French word and is connected with the idea of being hidden, i.e. the cache is used by the OS to help speed things up in a way that is hidden from ordinairy processes: programs do their stuff as normal, without worrying too much about details that happen behind the scenes. In other words, if you didn't know it is there, and it is working properly, you'd notice is an improvement in performance without it being obvious why.

---

