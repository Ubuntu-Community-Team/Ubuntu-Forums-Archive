---
title: "High memory usage"
date: 2012-02-24
forum: General Help
---

### Post by Subbeh on 2012-02-24
Hi, 

I recently installed Ubuntu 11.10 64bits on my notebook with 8gb of memory. After I use it for a while, all the memory gets used until there's nothing left. I don't run any processes which could take this much memory, except for maybe VirtualBox (2gb) and Firefox. When I close these, the memory usage is still very high: 
```
Tasks: 162 total,   2 running, 157 sleeping,   0 stopped,   3 zombie
Cpu(s):  0.6%us,  0.4%sy,  0.0%ni, 99.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8074096k total,  5346116k used,  2727980k free,    27636k buffers
Swap:  1951740k total,       44k used,  1951696k free,  4546676k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                     
 1821 steven    20   0  710m 116m  19m S    2  1.5   8:22.37 compiz                      
 1844 steven    20   0  580m  53m  11m S    0  0.7   0:08.36 dropbox                     
 1864 steven    20   0  480m  42m  17m S    0  0.5   0:14.40 gnome-do                    
 1839 steven    20   0  634m  40m  17m S    0  0.5   1:05.49 nautilus                    
 2159 steven    20   0  459m  35m  16m S    0  0.5   0:16.27 /usr/bin/termin             
 1841 steven    20   0  458m  31m  15m S    0  0.4   0:02.35 indicator-weath             
 2019 steven    20   0  401m  29m  10m S    0  0.4   0:20.04 unity-panel-ser             
 1836 steven    20   0  435m  25m  12m S    0  0.3   0:03.06 nm-applet                   
 2154 steven    20   0  245m  22m  10m S    0  0.3   0:10.15 applet.py                   
 1283 root      20   0  186m  22m 7380 S    1  0.3   9:24.25 Xorg                        
 2090 steven    20   0  203m  18m 7200 S    0  0.2   0:00.47 zeitgeist-daemo             
 1809 steven    20   0  587m  17m  11m S    0  0.2   0:08.94 gnome-settings-             
 1863 steven    20   0  284m  14m   9m S    0  0.2   0:03.88 notify-osd                  
 1837 steven    20   0  276m  13m  10m S    0  0.2   0:00.17 polkit-gnome-au             
 3278 steven    20   0  316m  12m 9.8m S    0  0.2   0:00.02 goa-daemon                  
```Is there any way to find out which processes are taking up all the memory? 

Thanks

---

### Post by snowpine on 2012-02-24
You may find this site helpful, it has instructions for finding your **actual** RAM usage (not RAM that is being used as cache to help your system run faster):

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by Subbeh on 2012-02-24
> **snowpine said:**
> You may find this site helpful, it has instructions for finding your **actual** RAM usage (not RAM that is being used as cache to help your system run faster):

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

Thanks for the reply snowpine. The strange thing is that when I was running MS Office in Wine, I got a message that some tasks could not be performed due to low memory. According to the site you posted this should not happen...

---

### Post by snowpine on 2012-02-24
Next time that happens, now you know the knowledge and tools to analyze your RAM usage.

However I feel compelled to point out that MS Office is not a Linux application provided or supported by Canonical. WINE is not a 100% perfect emulator, and so you might try checking the winehq website to see if other users have reported the same problem (and possibly a solution). The term "memory leak" is often used to describe when an application steals RAM from the operating system and won't give it back, that might help you with your search terms. :)

---

