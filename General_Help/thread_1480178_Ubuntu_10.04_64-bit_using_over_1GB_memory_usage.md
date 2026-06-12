---
title: "Ubuntu 10.04 64-bit using over 1GB memory usage"
date: 2010-05-11
forum: General Help
---

### Post by v4npro on 2010-05-11
Is this normal? I check system monitor and the top most is xorg followed by compiz.  When I first started with 10.04 few days ago it was around 300-500MB.  

Top:
[img]http://i39.tinypic.com/1z4y2q0.jpg[/img]

---

### Post by stormb on 2010-05-11
Your system appears to be using 822MB (remember that cache and buffers do not count as normal memory usage as they are automatically freed up if needed).

Your main culprits for memory usage appear to be firefix, compiz and f-spot, however we can't see the full story as your list is sorted by CPU and not memory usage. Open up top again and press '>'. This will sort by the next column along. You'll then be able to see for definite what is using up your memory (but again remember to deduct cache and buffers from the 'used' amount). Either way, it's not quite using 1GB.

Will

---

### Post by v4npro on 2010-05-11
I rebooted and now usage is down to 300-500MB.  Next time it goes close to 1gb I'll switch through "top" to show a screenshot of it.  Thanks for the reply.

---

### Post by alecz20 on 2010-06-21
I'm runnin 9.10.
Since I got to the computer, I only opened firefox, amule, and transmission, and the memory usage went from 850 MB to 1.5 GB in about 20 minutes, an it keeps growing.

If I look in System Monitor the sum of the memory usage of all processes seems to add to about 400 MB, I have no idea what is using the other 1000 MB.

here is the output of top (hi to low mem usage):

```

Tasks: 201 total,   1 running, 200 sleeping,   0 stopped,   0 zombie
Cpu(s): 13.1%us,  1.3%sy,  0.0%ni, 84.8%id,  0.6%wa,  0.2%hi,  0.0%si,  0.0%st
**Mem:   2052764k total,  1587008k used,   465756k free,    84820k buffers**
Swap:   779144k total,     1916k used,   777228k free,   382416k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5109 root      20   0  142m  89m  24m S   26  4.4   8:47.85 Xorg               
 6650 alecz     20   0  207m  70m  23m S    4  3.5   0:59.79 firefox            
 6644 alecz     20   0 73064  30m  10m S    2  1.5   0:21.32 transmission       
 6620 alecz     20   0  141m  28m  17m S    6  1.4   1:00.92 amule              
 5379 alecz     20   0 95888  26m  15m S    0  1.3   0:00.76 nautilus           
 5377 alecz     20   0 31192  22m 8040 S    1  1.1   1:03.78 compiz.real        
 5378 alecz     20   0 82024  21m  14m S    0  1.0   0:02.69 gnome-panel        
 6648 alecz     20   0 48892  20m  15m S   19  1.0   3:38.86 gnome-system-mo    
 5383 alecz     20   0 29436  14m 8200 S    0  0.7   0:00.10 python             
 6737 alecz     20   0 41904  12m 9532 S    0  0.6   0:00.51 gnome-terminal     
 5392 alecz     20   0 43884  12m 9628 S    0  0.6   0:00.19 gweather-applet    
 5436 alecz     20   0 35608  12m 9644 S    0  0.6   0:00.08 indicator-apple    
 5399 alecz     20   0 41836  11m 8488 S    0  0.6   0:00.15 nm-applet          
 5439 alecz     20   0 34792  11m 8584 S    0  0.6   0:00.06 indicator-apple    
 5410 alecz     20   0 68356  11m 8980 S    0  0.6   0:00.08 evolution-alarm    
 5412 alecz     20   0 30848  10m 8424 S    0  0.5   0:00.88 update-notifier    
 5501 alecz     20   0 44796  10m 8776 S    0  0.5   0:00.05 evolution-excha    
 5402 alecz     20   0 98096  10m 8196 S    0  0.5   0:00.07 gnome-volume-co    
 5394 alecz     20   0 33936  10m 7852 S    0  0.5   0:00.08 trashapplet        
 5434 alecz     20   0 24376  10m 8696 S    0  0.5   0:37.85 multiload-apple    
 5431 alecz     20   0 24200  10m 8480 S    0  0.5   0:00.57 cpufreq-applet     
 5285 alecz     20   0 97668 9.8m 6752 S    0  0.5   0:04.34 gnome-settings-    
 5406 alecz     20   0 29768 9512 7032 S    0  0.5   0:00.34 gnome-power-man    
 5443 alecz     20   0 19972 9424 7556 S    0  0.5   0:01.10 gtk-window-deco    
 3653 alex      20   0 70720 8880 6788 S    0  0.4   0:00.01 evolution-data-    
 5505 alecz     20   0 70724 8788 6728 S    0  0.4   0:00.03 evolution-data-    
 4105 root      20   0 11700 7376 3760 S    0  0.4   0:00.07 system-service-    
 5284 alecz     20   0 22500 7312 5304 S    0  0.4   0:00.06 seahorse-daemon    
 5384 alecz     20   0 19932 7232 5804 S    0  0.4   0:01.45 vino-server        
 5400 alecz     20   0 16972 6820 5564 S    0  0.3   0:00.04 bluetooth-apple    
 5210 alecz     20   0 25512 6584 5276 S    0  0.3   0:00.08 gnome-session      
 5409 alecz     20   0 17156 6440 5192 S    0  0.3   0:00.01 gdu-notificatio    
 5309 alecz     20   0 17444 6360 5164 S    0  0.3   0:00.04 notify-osd         
 5404 alecz     20   0 16548 5652 4592 S    0  0.3   0:00.00 polkit-gnome-au    
 5421 alecz     20   0 17572 5652 4284 S    0  0.3   0:01.57 gnome-screensav    
 5273 alecz     20   0  7884 4820 2188 S    0  0.2   0:00.50 gconfd-2           
 5265 alecz     20   0  107m 4532 3288 S    0  0.2   0:00.25 pulseaudio         
 1125 haldaemo  20   0  6172 4136 3448 S    0  0.2   0:00.15 hald               
 1235 root      20   0  8376 3712 3092 S    0  0.2   0:00.06 NetworkManager     
 5381 alecz     20   0 41688 3656 2660 S    0  0.2   0:00.04 bonobo-activati    
 6739 alecz     20   0  6352 3644 1504 S    0  0.2   0:00.10 bash               
 5195 alecz     20   0 41740 3576 2920 S    0  0.2   0:00.00 gnome-keyring-d    
 3158 root      20   0  5932 3536 2756 S    0  0.2   0:00.07 polkitd            
 5454 alecz     20   0  8288 3484 2744 S    0  0.2   0:00.06 indicator-messa    
 5108 root      20   0  8536 3416 2792 S    0  0.2   0:00.03 gdm-simple-slav    
 1380 root      20   0  8604 3336 2732 S    0  0.2   0:00.04 gdm-binary         
 5448 alecz     20   0 11960 3176 2608 S    0  0.2   0:00.01 indicator-statu    
 5414 alecz     20   0 15592 3124 2592 S    0  0.2   0:00.01 gvfs-gdu-volume    
alecz@alex-desktop:~$ 


```

you can see in the first line that over 1.5 GB is used, but WHERE and WHY?

---

