---
title: "top command memory usage"
date: 2010-01-24
forum: General Help
---

### Post by amsterdamharu on 2010-01-24
My top command shows the following:
```

top - 19:53:53 up  6:52,  3 users,  load average: 0.11, 0.18, 0.23
Tasks: 118 total,   1 running, 116 sleeping,   0 stopped,   1 zombie
Cpu(s):  9.8%us,  3.0%sy,  0.4%ni, 71.0%id, 14.6%wa,  0.4%hi,  0.8%si,  0.0%st
Mem:    904296k total,   867316k used,    36980k free,    22832k buffers
Swap:  2650684k total,    39896k used,  2610788k free,   508204k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND           
18704 user      20   0  147m  32m  17m S  6.0  3.6   0:08.86 vlc               
16168 user      20   0 30556 6092 3572 S  4.0  0.7   0:14.58 pulseaudio        
16190 user      20   0 15200 2692 1768 S  4.0  0.3   0:05.66 gnome-screensav   
17546 user      20   0 52328  16m  10m S  4.0  1.9   0:00.80 gnome-terminal    
16072 root      20   0  110m  45m  11m S  2.0  5.1   1:39.79 Xorg              
16260 user      20   0 78464  31m 9516 S  2.0  3.5   0:43.98 compiz.real       
    1 root      20   0  2844 1688  544 S  0.0  0.2   0:01.30 init              
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd          
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0       
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.10 ksoftirqd/0       
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0        
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.20 events/0          
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper           
   41 root      15  -5     0    0    0 S  0.0  0.0   0:01.86 kblockd/0         
   44 root      15  -5     0    0    0 S  0.0  0.0   0:19.72 kacpid            
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.84 kacpi_notify      
  174 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod          
```

Mem:    904296k total,   867316k used,    36980k free,    22832k buffers

867316/904296 = 96% used

Swap:  2650684k total,    39896k used,  2610788k free,   508204k cached
Swap is used so maybe running out of memory

In the list of applications I cannot see what is using all the memory:
18704 user      20   0  147m  32m  17m S  6.0  3.6   0:08.86 vlc               
16168 user      20   0 30556 6092 3572 S  4.0  0.7   0:14.58 pulseaudio        
16190 user      20   0 15200 2692 1768 S  4.0  0.3   0:05.66 gnome-screensav   
17546 user      20   0 52328  16m  10m S  4.0  1.9   0:00.80 gnome-terminal    
16072 root      20   0  110m  45m  11m S  2.0  5.1   1:39.79 Xorg              
16260 user      20   0 78464  31m 9516 S  2.0  3.5   0:43.98 compiz.real       
    1 root      20   0  2844 1688  544 S  0.0  0.2   0:01.30 init              

This shows only 17% of mem usage.

My question is; what is using the remaining 79%

---

### Post by Saiko Berry on 2010-01-24
Thats not how it works, don't worry xD

Mem:    960736k total,   937688k used,    23048k free,   133140k buffers

Same for me too.

htop is much better :p get htop. disable userlands trees in that though.

---

### Post by CharlesA on 2010-01-24
The output of top on my server looks similar, but is only using around 8% memory.

---

### Post by Saiko Berry on 2010-01-24
Like I said, just apt-get install htop, and use that instead. Its much better and configureable.

---

### Post by mcduck on 2010-01-24
Most of your memory is currently being used as disk cache, not by running applications. This part of RAM still counts as free from any program's point-of-view, since if a program needs more memory some cached data is dropped.

Mem:    904296k total,   867316k used,    36980k free,    22832k buffers
Swap:  2650684k total,    39896k used,  2610788k free,   508204k cached
904296k total - 508204k cache - 22832k buffers = 373260k of RAM used by the system and all your running programs.

If you don't want to calculate this yourself all the time then just run "free -m" and read from the "-/+ buffers/cache"-line to check the free RAM.

Also if you try to calculate the memory usage from the actual application data in top you'll want order the output based on RAM usage, not CPU, and also remember that you need to calculate it from the actal amount of memory used by all programs, not by the percentage (since things using less than 0,1% of RAM still use RAM) or just the apps that use most RAM.

---

### Post by OrangeCrate on 2010-01-24
**Linux Memory Management**

> Traditional Unix tools like 'top' often report a surprisingly small amount of free memory after a system has been running for a while...

[http://www.gentoo-wiki.info/FAQ_Linux_Memory_Management](http://www.gentoo-wiki.info/FAQ_Linux_Memory_Management)

---

### Post by amsterdamharu on 2010-01-24
Thank you all for the replies, I've noticed my system gets a bit sluggish when Transmission bittorrent client is running. Lots of disk io and programs don't respond as fast. Closing this program makes the system go back to normal.

---

### Post by warfacegod on 2010-01-24
> **amsterdamharu said:**
> Thank you all for the replies, I've noticed my system gets a bit sluggish when Transmission bittorrent client is running. Lots of disk io and programs don't respond as fast. Closing this program makes the system go back to normal.

With a Torrent client, that can be expected if your system specs are on the lower side. More RAM might be a help, according to top, you have about 1 GB.

---

