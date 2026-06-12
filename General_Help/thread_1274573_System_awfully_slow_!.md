---
title: "System awfully slow !"
date: 2009-09-24
forum: General Help
---

### Post by Raenk on 2009-09-24
Hi,

First I want to tell you that I have been using Linux for 5 years now.

I normally use another distro, which is much more complex. I had disk failure (secondary disk) in my computer at my office and decided to do a fresh install on the good remaining disk and to try an easier distro to have everything set up nice and easy, so I went with Ubuntu Jaunty. 

First days were nice, of course, I haven't got in anything yet to the system. But now it is awfully slow !

Before I go on, here are my specs:

AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
1 GB RAM (Corsair Extreme with very nice latency)
GeForce 6100 onboard

This is my top:

```

top - 15:09:20 up  2:51,  2 users,  load average: 0.75, 0.44, 0.37
Tasks: 135 total,   1 running, 134 sleeping,   0 stopped,   0 zombie
Cpu(s): 11.3%us,  3.1%sy,  0.0%ni, 85.4%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:    961928k total,   899480k used,    62448k free,    85672k buffers
Swap:   554232k total,   173032k used,   381200k free,   459620k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3610 raenk     20   0  466m 124m  25m S   10 13.3  24:08.41 firefox-bin        
 2808 root      20   0 79092  42m 9108 S    8  4.6  14:43.34 Xorg               
 8557 raenk     20   0 34444  15m  10m S    4  1.6   0:02.08 gnome-terminal     
 3277 raenk     20   0  156m 3680 2796 S    3  0.4   3:30.65 pulseaudio         
 5509 raenk     20   0 81312  40m  18m S    2  4.3   0:36.14 pidgin             
 3336 raenk     20   0 21268 9588 5848 S    1  1.0   0:03.63 notify-osd         
 3311 raenk     20   0 39276  14m 7232 S    0  1.5   0:33.96 gnome-panel        
 4217 raenk     20   0 41208  15m 8476 S    0  1.7   0:44.23 gedit              
 9176 raenk     20   0  2448 1188  912 R    0  0.1   0:00.05 top                
    1 root      20   0  3084  300  252 S    0  0.0   0:01.28 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.42 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:01.25 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         

```However, Gnome System Monitor shows:
**RAM 351.40 MB used of 939.40 MB and SWAP 169.0 MB used of 541.20 MB**

I do not have compiz (or any composition) thing enabled.
With that load, opening new firefox tabs is slow, minimizing and maximizing windows leave a trail, rendering web pages is slow, and well, opening anything else you can imagine.

You know my specs should not be giving any trouble and before, when using XP and my other distro anything was running smooth.

I have noticed some old posts and comments about Jaunty being slower than the previous release, but not much else is said.

Is there something well known about this among the community or mine and others are just isolated cases ?

Thanks for reading !

---

### Post by Raenk on 2009-09-25
Any ideas ?

---

