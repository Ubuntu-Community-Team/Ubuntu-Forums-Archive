---
title: "Quesiton About New Install"
date: 2010-03-01
forum: General Help
---

### Post by joek71 on 2010-03-01
Hi guys

I just installed Ubuntu 9.10 on a Dell Dimenssion 3000, here are the specs to the Dell:

2.8 GHz
Memory : 512
onboard Video card : Integrated Intel Extreme Graphics 2

And for some reason it is running very slugish, slow like not enough memory or cpu power.

Any suggestions?

Thanks in advance.

---

### Post by hwttdz on 2010-03-01
If you run "top" or "gnome-system-monitor" from the command line are there any processes that are eating up a high percentage of either cpu or memory?

---

### Post by joek71 on 2010-03-01
root - 37.1% Command: Xorg 2.2% Mem
Thats the most

---

### Post by hwttdz on 2010-03-01
I'm sorry it's hard to understand that, can you post the output of this command "top -b -n 1|head -n 20".  It appears that xorg might be eating 40ish percent of your cpu.

---

### Post by joek71 on 2010-03-01
Here is what i got:

mng@MNG:~$ top -b -n 1|head -n20
top - 15:54:42 up 4 min,  2 users,  load average: 0.57, 0.60, 0.28
Tasks: 143 total,   1 running, 142 sleeping,   0 stopped,   0 zombie
Cpu(s): 24.9%us,  8.0%sy,  1.9%ni, 56.0%id,  8.9%wa,  0.2%hi,  0.1%si,  0.0%st
Mem:    507648k total,   465356k used,    42292k free,    28504k buffers
Swap:  1485972k total,        0k used,  1485972k free,   236804k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
   34 root      15  -5     0    0    0 S  1.9  0.0   0:00.08 scsi_eh_1          
 1585 mng       20   0 63224  24m 7792 S  1.9  5.0   0:05.68 compiz.real        
 1677 mng       20   0 30068  11m 8976 S  1.9  2.4   0:00.95 awn-applet-acti    
 1798 mng       20   0  2468 1052  776 R  1.9  0.2   0:00.02 top                
    1 root      20   0  2532 1516 1128 S  0.0  0.3   0:01.33 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cpuset             
    8 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 netn

---

### Post by hwttdz on 2010-03-01
Looks pretty ok.  Has the behavior resolved itself?  What exactly is slow?  Also think you could wrap your previous post in [CODE] tags?

---

### Post by joek71 on 2010-03-01
Everyting is slow, I am using AWN i changed the look and feel of Ubuntu, and it is very slow. opening and closing of new apps, feels like something is hanging in the air.

---

### Post by hwttdz on 2010-03-01
So it's just the window open and window close animations which are slow?  Once programs are open (and there is not another opening or closing or using awn) then you're ok?  What if you close awn?

---

### Post by joek71 on 2010-03-01
I did Update Manager and i got this :
Error:

W.GPG error: [http://ppa.laucnhed.net](http://ppa.laucnhed.net) hardy Release. The following signature couldnt be verified because public key is not available:
NO_PUBLICKEY 7F2CA23BF810CD5

---

### Post by joek71 on 2010-03-01
closed AWN and still slow :confused:

---

