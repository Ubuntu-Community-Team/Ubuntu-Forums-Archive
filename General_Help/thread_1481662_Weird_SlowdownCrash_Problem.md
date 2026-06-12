---
title: "Weird Slowdown/Crash Problem"
date: 2010-05-12
forum: General Help
---

### Post by themattjon on 2010-05-12
My mother's computer was a Dell running on Windows XP. After a few years it started slowing down to the point of crashing often. It often took several minutes between a click of the mouse and it's reaction on the monitor!
I've finally convinced her to use a newer Dell with Ubuntu 9.10 installed. It worked great for a few weeks, but lately has started showing the same slowdown symptoms or even crashing (especially with Firefox). It seems odd to me that two different computers, with two different operating systems would both slow down to the point of crashing.
Nobody ever figured out what was wrong with the former. I figured it was just an old computer that couldn't keep up with XP updates anymore. But now this? With LINUX?!
Could there be some kind of external stimulus that's ruining the operation?
Any ideas?

---

### Post by mörgæs on 2010-05-14
> **themattjon said:**
> My mother's computer was a Dell running on Windows XP. After a few years it started slowing down to the point of crashing often. It often took several minutes between a click of the mouse and it's reaction on the monitor!

This is just normal for a Windows installation, but it does not indicate that the machine does not run well on Ubuntu. You could try booting a live Ubuntu and see how it works.

> **themattjon said:**
> 
I've finally convinced her to use a newer Dell with Ubuntu 9.10 installed. It worked great for a few weeks, but lately has started showing the same slowdown symptoms or even crashing (especially with Firefox). It seems odd to me that two different computers, with two different operating systems would both slow down to the point of crashing.
Nobody ever figured out what was wrong with the former. I figured it was just an old computer that couldn't keep up with XP updates anymore. But now this? With LINUX?!
Could there be some kind of external stimulus that's ruining the operation?
Any ideas?

Do the commands **top** and **free -m** indicate a heavy load on the system?

---

### Post by themattjon on 2010-05-14
This is what free -m gets me:

             total       used       free     shared    buffers     cached
Mem:           993        765        228          0         76        410
-/+ buffers/cache:        277        716
Swap:         2910          0       2910

I have two accounts on the PC, but technically only need one. Would deleting the other account pretty much double the space and run smoother?

---

### Post by mörgæs on 2010-05-16
> **themattjon said:**
> This is what free -m gets me:

```
              total       used       free     shared    buffers     cached
Mem:           993        765        228          0         76        410
-/+ buffers/cache:        277        716
Swap:         2910          0       2910
```I have two accounts on the PC, but technically only need one. Would deleting the other account pretty much double the space and run smoother?

Nothing unusual here. Does **top** indicate a heavy processor load?


An extra user account takes very little space (except for the files you are storing in it). It is not the reason for your machine being slow.

---

### Post by themattjon on 2010-05-17
Trying to get a copy from the Top command was tricky! It's all pretty much gibberish to me... Here goes:

top - 14:42:09 up  5:18,  3 users,  load average: 0.13, 0.15, 0.06
Tasks: 175 total,   1 running, 174 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.3%us,  1.0%sy,  0.0%ni, 95.3%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:   1017792k total,   975588k used,    42204k free,    70808k buffers
Swap:  2980016k total,        0k used,  2980016k free,   609400k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1908 root      20   0 35136  11m 6580 S  2.3  1.2   0:08.76 
    1 root      20   0  2532 1528 1128 S  0.0  0.2   0:01.18 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cpuset             
    8 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 netns              
   10 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 async/mgr          
   11 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0      
   12 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 kblockd/0          
   13 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid

---

### Post by mörgæs on 2010-05-18
It all looks fine. I don't have any specific advice, sorry. 

The unspecific advice would be just to do a fresh install (not upgrade) of Ubuntu. It will not tell you what was wrong, but it will give you a working computer.

---

### Post by themattjon on 2010-05-18
I might just do that with the latest version, thanks.

---

### Post by mörgæs on 2010-05-18
You are welcome. What about the old machine, did you try Ubuntu on it?

---

