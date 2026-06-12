---
title: "Ubuntu &amp; Samsung N148 : CPU maxed-out"
date: 2012-07-23
forum: General Help
---

### Post by ak4allz on 2012-07-23
Hi peers...

I'm the user for Samsung Netbook N148. Already installed Ubuntu 12.04 precise.

Done with the benchmarking process, I can say that the cpu always maxed-out from the indicator and I can feel the lagginess. Cold boot also takes a little bit longer (not too long but still you can feel the differences compared to older releases of Ubuntu).

Here's the spec of my netbook.
1. RAM : 2Gb
2. CPU : Intel Atom CedarTrail 1.6Ghz
3. Year : 2011
4. Distro : Ubuntu 12.04 LTS
5. Swap : yes, 500Mb

I'm not hoping for someone to solve my problems actually, but is there anyone who has the same experiences as me (noticeable lagginess, slow down, cpu often maxed out), kindly tell me in this thread :)

I'm looking forward to own a new laptop, maybe I will go for ASuS with AMD A6 as the CPU/APU soon.

Thanks :)

---

### Post by sanderj on 2012-07-23
To measure how (over)loaded your system is, you can use:

```
uptime
```

Look at the last three numbers: if they are above 1 (or 2), it means your system has "waiting processes", which is a sign of overloading.

```
top -bn1 | head -15

```will show your system usage, and the heavy processes.

You can also use the GUI tool "system monitor", and look at the tabs Processes and Resources.


Here's my system:

```
sander@R540:~$ uptime
 13:01:41 up 3 days, 17:18,  7 users,  load average: 0.73, 0.96, 0.98
sander@R540:~$ 
sander@R540:~$ 


sander@R540:~$ top -bn1 | head -15
top - 13:01:51 up 3 days, 17:18,  7 users,  load average: 0.77, 0.96, 0.98
Tasks: 240 total,   1 running, 229 sleeping,   0 stopped,  10 zombie
Cpu(s):  5.4%us,  7.0%sy,  0.0%ni, 85.6%id,  1.9%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   3843824k total,  3373672k used,   470152k free,    93328k buffers
Swap:  4881404k total,   363520k used,  4517884k free,   764544k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                           
16869 sander    20   0 1780m 110m  32m S    8  3.0  60:01.30 chromium-browse                                                                   
 1135 root      20   0  288m  46m  28m S    4  1.2  47:59.05 Xorg                                                                              
10241 sander    20   0 17460 1384  940 R    4  0.0   0:00.02 top                                                                               
 1815 sander    20   0  672m 8040 4296 S    2  0.2   6:59.59 metacity                                                                          
16786 sander    20   0 1184m 286m  23m S    2  7.6  12:43.71 chromium-browse                                                                   
22489 sander    20   0 1881m  70m  27m S    2  1.9   1:02.36 vlc                                                                               
29092 root      20   0     0    0    0 S    2  0.0   0:12.49 kworker/1:0                                                                       
    1 root      20   0 24432 1696  744 S    0  0.0   0:02.11 init                                                                              
sander@R540:~$ 
sander@R540:~$

```

---

### Post by mastablasta on 2012-07-23
what happens if you use Unity 2D? Is 500 mb the size of /swap? if so isn't that a bit low?

---

### Post by ak4allz on 2012-07-23
> **sanderj said:**
> To measure how (over)loaded your system is, you can use:

```
uptime
```

Look at the last three numbers: if they are above 1 (or 2), it means your system has "waiting processes", which is a sign of overloading.

```
top -bn1 | head -15

```will show your system usage, and the heavy processes.

You can also use the GUI tool "system monitor", and look at the tabs Processes and Resources.


Here's my system:

```
sander@R540:~$ uptime
 13:01:41 up 3 days, 17:18,  7 users,  load average: 0.73, 0.96, 0.98
sander@R540:~$ 
sander@R540:~$ 


sander@R540:~$ top -bn1 | head -15
top - 13:01:51 up 3 days, 17:18,  7 users,  load average: 0.77, 0.96, 0.98
Tasks: 240 total,   1 running, 229 sleeping,   0 stopped,  10 zombie
Cpu(s):  5.4%us,  7.0%sy,  0.0%ni, 85.6%id,  1.9%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   3843824k total,  3373672k used,   470152k free,    93328k buffers
Swap:  4881404k total,   363520k used,  4517884k free,   764544k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                           
16869 sander    20   0 1780m 110m  32m S    8  3.0  60:01.30 chromium-browse                                                                   
 1135 root      20   0  288m  46m  28m S    4  1.2  47:59.05 Xorg                                                                              
10241 sander    20   0 17460 1384  940 R    4  0.0   0:00.02 top                                                                               
 1815 sander    20   0  672m 8040 4296 S    2  0.2   6:59.59 metacity                                                                          
16786 sander    20   0 1184m 286m  23m S    2  7.6  12:43.71 chromium-browse                                                                   
22489 sander    20   0 1881m  70m  27m S    2  1.9   1:02.36 vlc                                                                               
29092 root      20   0     0    0    0 S    2  0.0   0:12.49 kworker/1:0                                                                       
    1 root      20   0 24432 1696  744 S    0  0.0   0:02.11 init                                                                              
sander@R540:~$ 
sander@R540:~$

```

Well thanks bro for the command lines. I will reCheck again the load and if I got some space, I will paste the results here.

> **mastablasta said:**
> what happens if you use Unity 2D? Is 500 mb the size of /swap? if so isn't that a bit low?

Nope, I didn't try yet the Unity 2D. So, 500Mb swap space considered as low for the linux (I mean, in this case, the Ubuntu Linux. Maybe different distro needs the different swap space, right? Such as the Arch Linux). If then, what will happen if I'm going to increase to swap space by using the swap file?

---

