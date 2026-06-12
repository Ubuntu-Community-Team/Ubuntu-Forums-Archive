---
title: "Questions"
date: 2009-11-25
forum: General Help
---

### Post by bryan4 on 2009-11-25
i have partition ubuntu 9.04 with win xp... and when i go into firefox and i tried to watch youtube videos it stops halfway.. and also in firefox when i go to some or alot of sites firefox closes on me for no reason.. i think i have 526 mb ram (i probably need to upgrade)... what do i do? this is really frustrating me.. also ubuntu is slow.. how do i make it a bigger partition the easy way?

---

### Post by Raff1 on 2009-11-25
You can open a terminal and run "top" to see how much memory applications like firefox is using. How much space did you give your /root and swap partition when you installed?

---

### Post by bryan4 on 2009-11-25
heres what it says:

mary@mary-desktop:~$ top

top - 16:57:29 up 46 min,  2 users,  load average: 0.38, 0.39, 0.42
Tasks: 112 total,   2 running, 110 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.0%us,  0.7%sy,  0.0%ni, 89.7%id,  3.7%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    249152k total,   245228k used,     3924k free,     7040k buffers
Swap:   176672k total,    88336k used,    88336k free,    91092k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2391 root      20   0  165m  15m 3188 S  3.7  6.3   5:36.00 Xorg               
 2949 mary      20   0 43652 4976 3656 S  2.0  2.0   0:07.85 metacity           
 4787 mary      20   0  2448 1172  912 R  0.7  0.5   0:00.03 top                
 4768 mary      20   0 33732  13m 9376 R  0.3  5.7   0:00.37 gnome-terminal     
    1 root      20   0  3084  168  120 S  0.0  0.1   0:01.37 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.08 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.03 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    8 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 kstop/0            
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0      
   10 root      15  -5     0    0    0 S  0.0  0.0   0:00.09 kblockd/0          
   11 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   12 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
   13 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue

---

### Post by Raff1 on 2009-11-25
> **bryan4 said:**
> heres what it says:


  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2391 root      20   0  165m  15m 3188 S  3.7  6.3   5:36.00 Xorg               
 2949 mary      20   0 43652 4976 3656 S  2.0  2.0   0:07.85 metacity           
 4787 mary      20   0  2448 1172  912 R  0.7  0.5   0:00.03 top                
 4768 mary      20   0 33732  13m 9376 R  0.3  5.7   0:00.37 gnome-terminal     
    
What you can see here is that Xorg is taking 3.7 % of your CPU and 6.3 % of your memory, the gnome terminal 0.3 % CPU, 5.7% MEM, etc.

So when you fire up firefox and browse a few tabs, or even play a youtube-video you can watch these percentages for the firefox process. If they shoots in the air you might have a issue with your CPU or Memory. 512 MB RAM should be more than sufficient to run firefox and Ubuntu. 

> Mem:    249152k total,   245228k used,     3924k free,     7040k buffers
Swap:   176672k total,    88336k used,    88336k free,    91092k cachedIt seems you might have a bit little free memory here. I am not good at interpreting this, but it seems you have only 1.57 % free memory or something. At my PC this percentage is much much higher. 

    249152k sounds like around 250 M. You sure you have 512 Mb RAM working? I have 2 Gb RAM and that number is accordingly high. My guess is that you only have 256 Mb memory working atm.

---

### Post by bryan4 on 2009-11-26
so.. how do i free memory?
How do i make ubuntu my main os and get rid of xp?

---

### Post by akakingess on 2009-11-26
> **bryan4 said:**
> so.. how do i free memory?
How do i make ubuntu my main os and get rid of xp?

Unfortunately, you can't really free up RAM, that's more of something you're going to have to spend the money to actually upgrade your RAM. First, check and make sure that 256MB is actually what you have, and then check to see how many slots you have with which to upgrade.  As far as getting rid of XP and going 100% Ubuntu, just run the LiveCD and do the installation and when it comes to partitioning, choose to use the entire drive, that will get rid of XP. Just be sure to back up whatever you want from Windows first, as well as the stuff from your Home folder within Ubuntu as well.  Hope this helps at least a little.

---

### Post by audiomick on 2009-11-26
> **Raff1 said:**
> . 

    249152k sounds like around 250 M. You sure you have 512 Mb RAM working? I have 2 Gb RAM and that number is accordingly high. My guess is that you only have 256 Mb memory working atm.

That's what I think too. It doesn't surprise me that you are having a bit of trouble with video stuff if that is all there is in there.

Bear in mind, running the installer as described in the previous post will also remove the existing Ubuntu installation.

---

