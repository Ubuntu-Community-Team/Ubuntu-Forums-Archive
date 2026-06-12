---
title: "CPU in System Monitor, Resources running at 100%"
date: 2012-08-22
forum: General Help
---

### Post by Peterfc on 2012-08-22
Hi

I recently had a post because the Software centre was not completing an install of Crossover. I marked as solved  but i now find that on further checking as to why my machine was running slow i find that my CPU is running at 100%. I am running a dual boot with windows 7 and Ubuntu 12.04. My machine has been slow since 12.04 was installed. This problem is only when i am using Ubuntu. I checked what was running at start-up and i have listed it with the System Monitor in the background. I also ran System monitor running on it's own and still 100% CPU. When i run Firefox Memory restart 1.10 often it says i have very little memory to use. At the time of the screen images nothing was running apart from the System monitor. I have searched on the Forum for slow running but found nothing that is of any help to me. 

Thanks for taking the time to read my post

Peter

I am using 12.04 Advent Laptop, 250gb hard drive, 3gb ram. Celeron 743@1.30 GHz. 



[http://ubuntuforums.org/showthread.php?t=2044268](http://ubuntuforums.org/showthread.php?t=2044268)

---

### Post by QIII on 2012-08-22
For those with low bandwidth, like me right now on a cell phone it would be nice to add thumbnails rather than entire images.  Use the paperclip above the input box to do that.

Would you please go to the terminal and post the results of 

```
top
```

because the images are killing me.

---

### Post by Peterfc on 2012-08-22
HI 

Sorry about the images.

Peter

top - 00:31:36 up  2:07,  2 users,  load average: 1.16, 1.35, 1.39
Tasks: 173 total,   2 running, 171 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.6%us, 50.8%sy, 46.5%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3058992k total,  1877440k used,  1181552k free,    95680k buffers
Swap:  3098620k total,        0k used,  3098620k free,  1222876k cached

 6854 root      25   5 76700  47m 6700 R 75.5  1.6  92:30.92 aptd               
21497 peter     20   0  511m 122m  33m S 14.5  4.1   8:34.29 firefox            
 1090 root      20   0 92852  22m 7240 S  4.0  0.7   5:16.25 Xorg               
 3231 peter     20   0  284m  76m  26m S  4.0  2.6   2:38.02 compiz             
 6703 root      20   0     0    0    0 S  1.3  0.0   0:15.78 kworker/0:0        
14925 peter     20   0  2836 1168  880 R  0.7  0.0   0:00.23 top                
    1 root      20   0  3504 2024 1352 S  0.0  0.1   0:00.75 init               
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S  0.0  0.0   0:00.28 ksoftirqd/0        
    6 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    7 root      RT   0     0    0    0 S  0.0  0.0   0:00.06 watchdog/0         
    8 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 cpuset             
    9 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 khelper            
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kdevtmpfs          
   11 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 netns              
   12 root      20   0     0    0    0 S  0.0  0.0   0:00.04 sync_supers        
   13 root      20   0     0    0    0 S  0.0  0.0   0:00.00 bdi-default

---

### Post by pqwoerituytrueiwoq on 2012-08-22
```
sudo aptd -r
```
give that a try

---

### Post by Peterfc on 2012-08-22
Hi 

Did that in a terminal and rebooted and the CPU usage is still 100%.

Thanks for trying.

Peter

---

### Post by Peterfc on 2012-08-23
Hi All

I have tried to reinstall 12.04 and i have tried to start Update-Manager -d but i get a message. 

Unable to get exclusive lock.
This usually means that another package management application ( like apt-get or aptitude  is already running ). Please close that application first.

I only have running.

Firefox to access the forum.
Terminal to access TOP
System Monitor to check usage.

My Laptop has almost ground to a halt. i am already to close applications that are not even open. 

Anybody know how to close application like apt-get or aptitude.

Peter :frown:

---

### Post by pqwoerituytrueiwoq on 2012-08-23
that error is cause aptd is still running, i suppose you could try kill the the process
i assume you have tried rebooting
sudo pkill -f aptd
there may be someway to reset it
disableing 3ed party sources may help
aptd manages the application database
you may be able to find something out in the log file viewer

---

