---
title: "Lag on Firefox"
date: 2010-05-12
forum: General Help
---

### Post by kshawkeye on 2010-05-12
I just installed Ubuntu 10.04 LTS, whenever I use firefox to browse to [http://psp.ign.com/](http://psp.ign.com/) my whole system will freeze, to the point of having to do a forceful shutdown of my system. Also, if I mange to move my glitching mouse cursor over to the close button while the page is loading I am able to shut down firefox in time for my machine to continue running, but after I close firefox like that my whole system is lagging. My windows wont even open for a few seconds after I click them, and then they pop open randomly afterwords once my system stops locking up from trying to open them. For the most part Ubuntu 10.04 will work like a charm if firefox isn't opened, but once it has been opened everything is slow, and not just slow as in a little lag, slow to the point of pulling hair. Any ideas?

Another thing I just realized while trying to scroll down to "Submit new thread", firefox glitches down bit by bit when scrolling.

---

### Post by Crafty Kisses on 2010-05-12
Hello,

While Firefox is open, go into a terminal and run:
```
top
```
Copy and paste that over here at the forums. Have you tried running any other browser with the same issue?

---

### Post by kshawkeye on 2010-05-12
[quote=Crafty Kisses]Hello,

While Firefox is open, go into a terminal and run:
 	Code:
 	top 
[/quote]  	

This is what it came up with.

> 
top - 22:10:15 up 2 min,  3 users,  load average: 0.94, 0.62, 0.25
Tasks: 158 total,   1 running, 157 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.3%us,  2.0%sy,  0.0%ni, 91.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2052964k total,   413832k used,  1639132k free,    36484k buffers
Swap:  1648632k total,        0k used,  1648632k free,   172344k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                
 1427 kyle      20   0 47492  13m  10m S  4.3  0.7   0:01.33 gnome-terminal                         
  992 root      20   0 39376  20m 8408 S  1.7  1.0   0:11.18 Xorg                                   
 1294 kyle      20   0 70192  25m 8936 S  1.3  1.3   0:02.48 compiz                                 
 1458 kyle      20   0  296m  64m  25m S  0.7  3.2   0:09.08 firefox-bin                            
 1522 kyle      20   0  2544 1216  908 R  0.3  0.1   0:00.16 top                                    
    1 root      20   0  2796 1612 1164 S  0.0  0.1   0:00.47 init                                   
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd                               
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0                            
    4 root      20   0     0    0    0 S  0.0  0.0   0:00.06 ksoftirqd/0                            
    5 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                             
    6 root      20   0     0    0    0 S  0.0  0.0   0:00.07 events/0                               
    7 root      20   0     0    0    0 S  0.0  0.0   0:00.00 cpuset                                 
    8 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khelper                                
    9 root      20   0     0    0    0 S  0.0  0.0   0:00.00 netns                                  
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.00 async/mgr                              
   11 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pm                                     
   12 root      20   0     0    0    0 S  0.0  0.0   0:00.00 sync_supers                            
   13 root      20   0     0    0    0 S  0.0  0.0   0:00.00 bdi-default                            
   14 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                          
   15 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kblockd/0                              
   16 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kacpid                                 
   17 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                           
   18 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kacpi_hotplug                          
   19 root      20   0     0    0    0 S  0.0  0.0   0:00.04 ata/0                                  
   20 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                
   21 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                          
   22 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khubd                                  
   23 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kseriod                                
   24 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kmmcd                                  
   27 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khungtaskd                             
   28 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                
   29 root      25   5     0    0    0 S  0.0  0.0   0:00.00 ksmd                                   
   30 root      20   0     0    0    0 S  0.0  0.0   0:00.00 aio/0                                  
   31 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ecryptfs-kthrea                        


[quote=Crafty Kisses]Have you tried running any other browser with the same issue?[/quote]

No.

---

### Post by oleink on 2010-05-12
> **kshawkeye said:**
> This is what it came up with.





No.

If you do try another browser try chromium.  I tried it and now i barely use firefox

---

### Post by robertcoulson on 2010-05-12
oleink is right...try Google Chrome..Had the same problems as you with Firefox..Now I use Chrome all the time with no problems.
Robert

---

### Post by kshawkeye on 2010-05-13
[quote=robertcoulson]try Google Chrome..Had the same problems as you with Firefox..Now I use  Chrome all the time with no problems.[/quote]

I tried google chrome, other then the odd fact that every time I reboot it disappears from my Applications>Internet menu, I thought it was working. Sadly, it isn't just my internet browser, it seems that any time my machine is lagged one time, for the rest of the time it remains booted it will lag, horribly. I tried opening Amarok and got that one time lag from it loading, everything on my machine there after was lagging, even after Amarok was closed.

---

### Post by pqwoerituytrueiwoq on 2010-05-13
it is because of flash
1. you can use adblock and block teh ads that make it lag
2. remove flash player
3. run firefox on a ram disk (yes that improved flash performance for me)

i use 1 and 3

---

### Post by wojox on 2010-05-13
Try this out [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by kshawkeye on 2010-05-13
[quote=pqwoerituytrueiwoq]it is because of flash[/quote]

I uninstalled flash just to test this theory, and the problem still remains, it's not flash.

[quote=wojox]Try this out [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")[/quote]

The problem is not only on firefox, it is with my whole system. Originally it was only firefox or I only noticed it on firefox while scrolling, but now I can tell its effecting my whole system.

---

### Post by wojox on 2010-05-13
> **kshawkeye said:**
> 
The problem is not only on firefox, it is with my whole system. Originally it was only firefox or I only noticed it on firefox while scrolling, but now I can tell its effecting my whole system.

Are you using a router or switch? Try disabling IPv6 [http://wojox.homelinux.org/?p=46](http://wojox.homelinux.org/?p=46)

---

