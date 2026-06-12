---
title: "Hard Drive abuse by Karmic (usually when using firefox/chrome)"
date: 2009-12-17
forum: General Help
---

### Post by KitchenKnif on 2009-12-17
Recently, Karmic has been abusing the hard drive. I mean abusing it to the point that the whole system comes to a complete stop for several seconds...
And the longer the computer is running, the more this happens.

This generally happens during firefox/chrome sessions, but is not restricted to them. 

I generally have firfox/chrome, Banshee & Deluge open at the same time.

around 80% of my 1GB of ram is generally in use, and about 20% of my 2GB of swap. 

Any ideas?

---

### Post by QIII on 2009-12-17
That sort of resource use seems excessive.

Let's start with something pretty basic, and move on if we need to.  (Sorry if this seems too basic.  I don't mean to patronize, I simply don't know your level of expertise.)

In the termimal, type "top" (no quotes).

After top starts, press Cntl+C to get it to stop refreshing.

Highlight the text and press Cntl+Shift+C to copy the text.

Paste the results back here inside code tags.

---

### Post by KitchenKnif on 2009-12-17
```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4030 rustynai  20   0  940m 139m 9192 S   13 13.9  47:45.00 banshee-1          
 2541 rustynai  20   0  130m 3788 1800 D    5  0.4   2:54.02 trackerd           
20164 rustynai  20   0  585m  89m  18m S    3  9.0   2:32.69 firefox            
 2423 rustynai   9 -11  398m  14m  13m S    2  1.4  21:01.69 pulseaudio         
 1463 root      20   0  687m  68m 5136 S    2  6.9  38:55.72 Xorg               
 4108 rustynai  20   0  480m  16m 6292 S    2  1.7   7:19.84 deluge             
 6901 rustynai  20   0 98.0m 2040 1304 S    2  0.2   4:19.42 conky              
 2480 rustynai  20   0  310m  10m 7292 S    1  1.0   8:54.00 compiz.real        
16257 rustynai  20   0  243m 6088 3956 S    1  0.6   0:02.93 gnome-terminal     
23383 rustynai  20   0  435m  34m 7572 S    1  3.5   1:01.84 docky              
 5302 rustynai  20   0  622m  18m  11m S    1  1.9   0:31.22 empathy            
10938 couchdb   20   0  2280    4    0 D    1  0.0   0:00.02 beam.smp           
 2542 rustynai  20   0  197m 3608 2564 S    0  0.4   0:02.86 update-notifier    
 2569 rustynai  20   0  374m  27m 4652 S    0  2.8   0:36.49 gnome-do           
 4498 rustynai  20   0  284m  27m 4308 S    0  2.8   6:27.10 deluged            
10933 rustynai  20   0 19132 1368  980 R    0  0.1   0:00.04 top                
    1 root      20   0 19460 1080  744 S    0  0.1   0:04.96 init  
```

---

### Post by QIII on 2009-12-17
There is some text above that.  If you could run it again and include the entire output, it would be helpful.

Just using a calculator, it looks like as of that snapshot you were using 34% of your CPU and 47% of your memory (but some interesting numbers under VIRT).

EDIT:  Re your 1GB of memory.  Do you have an integrated GPU?  That could be reserving a lot of your memory, depending on whether you have allowed it to do so.

The upper portion of the output would give totals.

I have a suspicion that has panned out a number of times in the past.  vino often does not show in top, or it shows with 0 resources used.  Do you have desktop sharing enabled?

---

### Post by KitchenKnif on 2009-12-17
oops. forgot that bit.
for the old run:
```
top - 22:54:37 up  9:02,  2 users,  load average: 0.53, 0.40, 0.72
Tasks: 175 total,   1 running, 174 sleeping,   0 stopped,   0 zombie
Cpu(s): 12.8%us,  3.7%sy,  0.0%ni, 38.1%id, 44.6%wa,  0.2%hi,  0.5%si,  0.0%st
Mem:   1023256k total,  1014376k used,     8880k free,     4584k buffers
Swap:  1951856k total,   498064k used,  1453792k free,   119052k cached

```

new run:
```
top - 23:26:06 up  9:34,  2 users,  load average: 1.19, 0.68, 0.63
Tasks: 175 total,   3 running, 172 sleeping,   0 stopped,   0 zombie
Cpu(s): 18.3%us,  8.2%sy,  0.6%ni, 61.7%id, 10.7%wa,  0.1%hi,  0.3%si,  0.0%st
Mem:   1023256k total,  1009608k used,    13648k free,     1396k buffers
Swap:  1951856k total,   513792k used,  1438064k free,    96952k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4108 rustynai  20   0  480m  15m 5364 S    4  1.6   7:37.53 deluge             
 2423 rustynai   9 -11  398m  14m  13m S    2  1.4  21:35.98 pulseaudio         
 5302 rustynai  20   0  622m  17m  10m S    2  1.7   0:39.23 empathy            
27953 rustynai  20   0 19128 1260  884 R    2  0.1   0:00.03 top                
    1 root      20   0 19460 1068  732 S    0  0.1   0:05.16 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.21 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.28 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.25 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:02.78 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.06 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.25 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 cpuset             
   12 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   13 root      15  -5     0    0    0 S    0  0.0   0:00.00 netns   
```

Nah, I have dedicated nVidia GeForce 9400 with 512mb of it's own ram, so it isn't the GPU...

Desktop sharing... if it's disabled by default then it should be disabled... don't remember ever touching it :-/.

---

### Post by dcstar on 2009-12-17
> **KitchenKnif said:**
> Recently, Karmic has been abusing the hard drive. I mean abusing it to the point that the whole system comes to a complete stop for several seconds...
And the longer the computer is running, the more this happens.
........

Why do you think it is "abusing the hard drive"?

If your hard drive stalls your system, it is (usually) because bad sectors on your hard drive are causing the problem.

---

### Post by audiomick on 2009-12-17
Hallo
My  2 cents worth.
I reckon it sounds like hardware too. Given that it seems to get worse with time, it could also be something getting warm.
Indicator: if a restart fixes it immediately, it is possibly software related, or the aforementioned bad sectors or whatever. If it needs a rest before it is good again, it might be heat.

---

### Post by paradigm2 on 2009-12-17
> **audiomick said:**
> Hallo
My  2 cents worth.
I reckon it sounds like hardware too. Given that it seems to get worse with time, it could also be something getting warm.
Indicator: if a restart fixes it immediately, it is possibly software related, or the aforementioned bad sectors or whatever. If it needs a rest before it is good again, it might be heat.

I know on Karmic he can go to System -> Administration -> Disk Utility where it should indicate the health of the hard drive using the S.M.A.R.T. status.  Pretty neat utility.

---

### Post by brookie on 2009-12-17
Just another observation on my end. It may or may not help. 

I was using banshee, ff, deluge, tbird. I would run top and then I would minimize or maximize banshee and keep my top in the foreground. 

Every time I did this banshee would take tons of cpu and so would Xorg. The same thing happened with tbird. 

I switched to rhythmbox and evolution and no more hangs and slovenly slow non responsive system. Banshee and Tbird just seems to make xorg creep up on the cpu cycles when it minimized, maximized, opened or closed, or files scrolled in either app for some reason. At least on my system. 

I have desktop effects turned off as well.

Cheers, 
brook

---

### Post by aklo on 2009-12-17
Are you going to flash sites?

I do have problems with flash in firefox. I notice my dual core processor usage can range anywhere from 20-80%(changes every seconds) when i have flash in firefox(neopets games :)).

When i browse other sites, my processor usage immediately dropped to below 10%.

---

### Post by KitchenKnif on 2009-12-17
> **audiomick said:**
> Hallo
My  2 cents worth.
I reckon it sounds like hardware too. Given that it seems to get worse with time, it could also be something getting warm.
Indicator: if a restart fixes it immediately, it is possibly software related, or the aforementioned bad sectors or whatever. If it needs a rest before it is good again, it might be heat.

Yeah, a restart fixes it completely, so I think 'tis software-related. (Also, the HD's relatively new, so I hope it isn't dying on me already...)
S.M.A.R.T. also says it's 'healthy'...


> **brookie said:**
> Banshee and Tbird just seems to make xorg creep up on the cpu cycles when it minimized, maximized, opened or closed, or files scrolled in either app for some reason. At least on my system. 


The thing is, my cpu usage generally doesn't go over 30-40%, so i'm quite sure it's the hd usage...

---

