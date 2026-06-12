---
title: "My CPU Randomly Jumps to 100%"
date: 2010-09-19
forum: General Help
---

### Post by thesciencefreak on 2010-09-19
I am currently running Ubuntu 10.10 x32 on an Acer AMD Athlon x2 64.  I can be using the computer, or it can be idle, when I hear the fan kick on (very loud) and the system monitors show the CPU at 100%.  The problem started after an update in 10.04; updated to 10.10 and the problem has continued.  I am a newbie- and not the most experienced with computers- so I thank you in advance for your patience.

---

### Post by mbobak on 2010-09-19
So, you need to see what is using that CPU, when that happens.

One way to do that is, when the problem occurs, open a Terminal, and type 'top'.

Top will show you the top CPU consuming processes.  It runs in a loop, updating every few seconds.  Hit 'q' to exit.

When you know what's causing the problem, post that here, and we may be able to help you determine what the root cause is.

-Mark

---

### Post by thesciencefreak on 2010-09-19
Sorry- fresh install of 10.04 (~the beginnig of July); update to 10.10 yesterday (Saturday).

---

### Post by thesciencefreak on 2010-09-19
Here is the top output:


tony@desktop:~$ top

top - 21:12:23 up 30 min,  2 users,  load average: 5.84, 2.39, 1.06
Tasks: 166 total,   2 running, 164 sleeping,   0 stopped,   0 zombie
Cpu(s): 99.7%us,  0.2%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   2836188k total,   886616k used,  1949572k free,    68196k buffers
Swap:  8307708k total,        0k used,  8307708k free,   325928k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1611 tony      20   0  214m 115m  14m S  196  4.2   3:36.35 gnome-do           
 1357 root      20   0 63676  46m  13m S    3  1.7   0:53.59 Xorg               
 1572 tony      20   0  147m  43m  22m S    0  1.6   0:01.60 nautilus           
 1602 tony      20   0 67584  45m  13m S    0  1.6   0:08.91 compiz             
 1905 tony      20   0 96904  13m  10m S    0  0.5   0:02.27 gnome-terminal     
 1931 tony      20   0  2624 1136  832 R    0  0.0   0:05.36 top                
    1 root      20   0  2876 1632 1168 S    0  0.1   0:00.57 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:00.03 ksoftirqd/0        
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      20   0     0    0    0 S    0  0.0   0:00.14 ksoftirqd/1        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      20   0     0    0    0 S    0  0.0   0:00.02 events/0           
   10 root      20   0     0    0    0 S    0  0.0   0:00.03 events/1           
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset             

This is the second instance, and in both cases it is gnome do.

---

### Post by 3Miro on 2010-09-19
```

1611 tony 20 0 214m 115m 14m S 196 4.2 3:36.35 gnome-do 

```

Now you know which program gives you the trouble. Now you have to see what is it that you are doing with Gnome-Do specifically at that time.

---

### Post by thesciencefreak on 2010-09-19
I had gnome do set to run at startup, so it was running in the background, but I was not actively using it at the time.  I did quit the program, and the CPU usage returned to normal immediately.

---

### Post by 3Miro on 2010-09-19
> **thesciencefreak said:**
> I had gnome do set to run at startup, so it was running in the background, but I was not actively using it at the time.  I did quit the program, and the CPU usage returned to normal immediately.

I don't use Gnome-do, so I am not sure if this is a bug or if Gnome-do was doing something that it thought was useful. At any rate, this should fix the problem.

---

