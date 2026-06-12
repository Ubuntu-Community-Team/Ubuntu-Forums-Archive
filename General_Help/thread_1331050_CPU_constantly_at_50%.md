---
title: "CPU constantly at 50%"
date: 2009-11-18
forum: General Help
---

### Post by Zalbor on 2009-11-18
Exactly as the title says: my CPU is constantly working at 50% and never drops any below that. It's a dual core, and both cores are at 50% all the time.
This is an Acer 5920G, and this problem just began a few days ago. Before that it would be at almost 0% when idle.
I'm using 9.04.

I have another computer (single core) that Ubuntu 9.04 used to be installed on (but not right now) and it had the same issue; it suddenly began a few months ago but before that it was fine as well.

It's very annoying, the fan won't even shut down at all. What could be causing this?

Here's some output of top:
```
top - 06:15:39 up 22 min,  2 users,  load average: 2.51, 2.48, 1.89
Tasks: 147 total,  15 running, 132 sleeping,   0 stopped,   0 zombie
Cpu(s): 33.7%us, 21.3%sy,  0.0%ni, 44.8%id,  0.0%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   2060728k total,   826676k used,  1234052k free,    60884k buffers
Swap:   524280k total,        0k used,   524280k free,   388832k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3285 root      20   0  347m  39m  11m R   15  2.0   3:13.58 Xorg               
 3899 yorghos   20   0  3176 1328  652 S    5  0.1   1:00.09 dbus-daemon        
 3763 yorghos   20   0 26544 7280 5708 R    4  0.4   0:42.93 x-session-manag    
 3931 yorghos   20   0 75972  48m  13m S    4  2.4   0:38.64 compiz.real        
 3907 yorghos   20   0  8248 5136 2188 S    3  0.2   0:38.46 gconfd-2           
 4781 yorghos   20   0 16704 2952 1772 R    2  0.1   0:16.26 gnome-screensav    
 3925 yorghos   20   0 30492  10m 6976 R    1  0.5   0:18.15 gnome-settings-    
  305 yorghos   20   0     0    0    0 R    1  0.0   0:00.03 vino-server        
 4177 yorghos   20   0 23256 9780 7376 S    1  0.5   0:19.31 indicator-apple    
32038 yorghos   20   0 34484  14m 9.8m S    1  0.7   0:00.49 gnome-terminal     
 3953 yorghos   20   0 67416  11m 9688 R    1  0.6   0:04.35 evolution-alarm    
 3965 yorghos   20   0 16172 6608 5440 R    1  0.3   0:03.27 bluetooth-apple    
 3967 yorghos   20   0 27724  11m 7540 S    1  0.6   0:06.99 gnome-power-man    
15620 yorghos   20   0  320m 102m  28m R    1  5.1   0:53.20 firefox-3.5        
   22 root      15  -5     0    0    0 S    0  0.0   0:00.12 ata/1              
 3933 yorghos   20   0  5624 2140 1808 S    0  0.1   0:02.87 gvfsd              
 3934 yorghos   20   0 45664  20m  14m R    0  1.0   0:16.24 gnome-panel
```

---

### Post by QIII on 2009-11-18
Try shutting down vino (desktop sharing).

Despite what it seems to say in top, vino is a hog.

---

### Post by Sin@Sin-Sacrifice on 2009-11-18
Hrm... I was thinking compiz was the culprit but he could be right about vino too. Look in system monitor and see if things match up.

---

### Post by lavinog on 2009-11-19
htop might be better to use.

Try sorting by cpu%

---

### Post by DeMus on 2009-11-19
Get rid of Compiz and set the effects to none.
What you see in top is that Xorg takes a lot of the cpu and so is Compiz itself. What Xorg is doing is because of Compiz.
Which graphic card do you have and which driver is installed?
When you don't use the correct driver the CPU is doing tasks for the GPU as well.
But loose Compiz and things will be better.

---

### Post by doas777 on 2009-11-19
the numbers do not appear to add up. sometimes processes don't show in top/htop/iotop/iftop unless run as sudo. it may turn up some hidden stuff. otherwise, check for rootkits.
it could also be interupt processing. are you sure of your hardware?

---

### Post by Zalbor on 2009-11-19
Vino was totally it; thanks a lot! I'd forgotten I left it on.

By the way, the "top" I posted was run as root anyway.

---

