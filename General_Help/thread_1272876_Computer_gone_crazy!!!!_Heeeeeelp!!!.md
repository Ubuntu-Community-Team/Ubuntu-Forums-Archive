---
title: "Computer gone crazy!!!! Heeeeeelp!!!"
date: 2009-09-22
forum: General Help
---

### Post by Luca_turicci on 2009-09-22
HI, My computer's gone crazy, it keeps popping windows!!!! it says "launching file manager" or something like that, my ubuntu is in spanish. I first thought it had something to do with Ubuntu tweak, I uninstalled it but nothing happens, then deleted Screenlets, and NOTHING =S I don't know what to do or how to know what's causing it!, HELP!!

Here's a screenshot:

[IMG]http://img23.imageshack.us/img23/9463/pantallazoku.png[/IMG]

---

### Post by ks07 on 2009-09-22
My first suggestion would be a reboot, it seems that some script has gone wrong and is continuously spawning nautilus windows. A restart should probablly be enough if you haven't tried already.

Otherwise, could you post the output of ```
top
``` (ran in a terminal window) please, it may give an indication of what is happening.

---

### Post by credobyte on 2009-09-22
I would check my bash history asap :D If seriously, restart your PC & get back to us with what you have there.

---

### Post by Luca_turicci on 2009-09-22
here's the output of top

luca@luca-laptop:~$ top

top - 18:23:03 up 4 min,  2 users,  load average: 4.15, 2.38, 0.98
Tasks: 142 total,   3 running, 138 sleeping,   0 stopped,   1 zombie
Cpu(s): 57.4%us, 15.5%sy,  0.0%ni, 24.7%id,  1.1%wa,  1.0%hi,  0.2%si,  0.0%st
Mem:   1018216k total,   492516k used,   525700k free,    30740k buffers
Swap:  2980016k total,        0k used,  2980016k free,   238524k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1618 root      20   0 42004  15m 8632 D   30  1.5   0:55.49 Xorg               
 3312 luca      20   0 43712  13m  10m R   16  1.3   0:00.49 nautilus           
 2440 luca      20   0 69348  29m 8348 R   16  3.0   0:29.40 compiz.real        
 2877 luca      20   0  249m  67m  23m S   15  6.8   0:26.41 firefox            
 2441 luca      20   0 47140  21m  15m S   12  2.1   0:24.54 gnome-panel        
 3164 luca      20   0 37716  13m 9.8m S    6  1.4   0:01.75 gnome-terminal     
 2614 luca      20   0 81724  35m  15m S    4  3.6   0:13.90 python             
 2331 luca      20   0  3132 1148  596 S    3  0.1   0:05.92 dbus-daemon        
 2342 luca      20   0  7968 4544 2268 S    3  0.4   0:05.98 gconfd-2           
 1433 messageb  20   0  3336 1500  748 S    2  0.1   0:03.86 dbus-daemon        
 2347 luca      20   0 99256 9.8m 7932 S    2  1.0   0:02.56 gnome-settings-    
 2290 luca      20   0 27376 6960 5572 S    1  0.7   0:01.84 gnome-session      
 2443 luca      20   0 20728 9096 6976 S    1  0.9   0:01.49 emerald            
 2455 luca      20   0 36268  13m 9468 S    1  1.4   0:02.21 nm-applet          
 2466 luca      20   0 26308 9948 6880 S    1  1.0   0:01.35 gnome-power-man    
 1449 haldaemo  20   0  6764 4184 3436 S    0  0.4   0:00.56 hald               
 1471 root      20   0 20816 3064 2200 S    0  0.3   0:00.90 console-kit-

HOW THE HELL DO I CHECK BASH HISTORY?

---

### Post by credobyte on 2009-09-22
> **Luca_turicci said:**
> 
HOW THE HELL DO I CHECK BASH HISTORY?

```
history
```

:lolflag:

---

### Post by Luca_turicci on 2009-09-22
well, i'm looking at the history, it says the last thing i did was TOP, before that it was installing inkscape... ._. i haven't used inkscape in days.

---

