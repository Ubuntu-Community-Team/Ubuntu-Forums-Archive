---
title: "Dual core 100% CPU usage"
date: 2010-05-27
forum: General Help
---

### Post by X-Windows on 2010-05-27
Interested to find out if this is normal or not. I am running a Intel Core 2 Duo processor and the system monitor keeps showing one of the cores at 100%, and the other fluxuating normally. Is this normal or a bug with the system monitor. I am running Compiz, but that is pennies to the comp. It seems that about every 1.5 minutes the cores "swap" the 100% usage, but it always ends up with one core at 100% and the other core doing normal stuff.

---

### Post by jerrrys on 2010-05-27
system monitor can give misleading readings.  open a terminal and enter **top** and see what you get.

---

### Post by X-Windows on 2010-05-27
From the results of **top** it seems like everything is normal, however what do the parts **49.3%id**, and  **42.5%wa** mean?

```

~$ top

top - 18:16:36 up 1 min,  2 users,  load average: 0.75, 0.24, 0.08
Tasks: 179 total,   1 running, 178 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.1%us,  3.6%sy,  0.0%ni, **49.3%id**, **42.5%wa**,  0.5%hi,  0.0%si,  0.0%st
Mem:   4055688k total,   597072k used,  3458616k free,    38476k buffers
Swap:  3905528k total,        0k used,  3905528k free,   184252k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1600 Username   20   0  227m  20m 9.8m S    4  0.5   0:00.13 python             
 1599 Username   20   0  424m  13m  10m S    3  0.3   0:00.08 evolution-alarm    
 1605 Username   20   0  381m  10m 7948 S    2  0.3   0:00.07 evolution-data-    
 1418 Username   20   0  311m  60m  23m S    1  1.5   0:00.88 compiz             
 1610 Username   20   0  349m  13m  10m S    1  0.3   0:00.04 evolution-excha    
 1398 Username   20   0 46076 5612 2392 S    1  0.1   0:00.19 gconfd-2           
 1456 root      20   0 57288 3368 2576 S    1  0.1   0:00.06 udisks-daemon      
  853 messageb  20   0 24232 1760  772 S    0  0.0   0:00.15 dbus-daemon        
 1147 root      20   0  126m  35m  18m S    0  0.9   0:04.48 Xorg               
 1395 Username   20   0 24072 1456  604 S    0  0.0   0:00.13 dbus-daemon        
 1404 Username   20   0  306m  10m 7748 S    0  0.3   0:00.07 gnome-settings-    
    1 root      20   0 23776 1956 1268 S    0  0.0   0:00.48 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.01 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        

```

---

### Post by jerrrys on 2010-05-27
beats me what that means, hardly ever use 'top'... :)

---

### Post by jerrrys on 2010-05-27
[attach]158464[/attach]

---

### Post by oleink on 2010-05-27
> **X-Windows said:**
> Interested to find out if this is normal or not. I am running a Intel Core 2 Duo processor and the system monitor keeps showing one of the cores at 100%, and the other fluxuating normally. Is this normal or a bug with the system monitor. I am running Compiz, but that is pennies to the comp. It seems that about every 1.5 minutes the cores "swap" the 100% usage, but it always ends up with one core at 100% and the other core doing normal stuff.

Are you sure it isn't displaying a "Cpu 0" this often happens for me but actually has nothing to do with my cpus in fact I have no idea what it is but I've got a dual core and cpu 1 and 2 are never at 99% but this thing cpu0 always is

---

### Post by Seq on 2010-05-27
> **X-Windows said:**
> From the results of **top** it seems like everything is normal, however what do the parts **49.3%id**, and  **42.5%wa** mean?

%id is idle, %wa is io wait ("Amount of time the CPU has been waiting for I/O to complete.")

`man top` and search for "CPU States" for more info.

---

### Post by X-Windows on 2010-05-27
Just rebooted and that seemed to fix it for the time being. Cpu1 and 2 are hovering at around 20% now. I had finished installing several patches via the terminal, downloading some programs through the Ubuntu Software Center and did some work on a word document when I checked the system monitor. It was most peculiar, the processes tab looked normal, but the resources tab showed the cpu's "sharing" the 100% load, every ~60 seconds the graphs would form an X as the processors swapped the 100%. I downloaded some kind of CPU temperature gague that showed both processors at 66 degrees Celsius, in contrast now they are at around 39. 

Glad to see the problem seems to have resolved itself, I was pretty worried that Ubuntu/Compiz was a huge resource hog.

---

