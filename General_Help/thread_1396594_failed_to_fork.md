---
title: "failed to fork"
date: 2010-02-02
forum: General Help
---

### Post by drew boardman on 2010-02-02
Hi all,

Recently I have been getting this msg when I click on a link or try and open an attachment from within Evolution. 

 Failed to fork (Cannot allocate memory)

I had the problem a while but thought when I do a clean install it would go away.  I had been upgrading the last 2 releases.  However it hasn't.

So to recap, Koala (Clean install) on a EEE PC 901 2GB Ram.

Thanks for the help.

Drew

---

### Post by drew boardman on 2010-02-06
So, nobody knows,then?
I guess I'll keep waiting.
Drew

---

### Post by gmargo on 2010-02-06
Inadequate swap space probably.  Keep a window open with **top** running so you can check your swap usage and see who is hogging memory.

---

### Post by drew boardman on 2010-02-15
Hi,

Thanks for the response.

I have 501MB swap partition.  It use to work fine.

I do not understand the part "Keep a window open with top running".

Whats top?

Thanks

Drew

---

### Post by howlingmadhowie on 2010-02-15
open a terminal and enter the command "top". this will show a list of all active processes and how much memory they're using.

---

### Post by drew boardman on 2010-02-15
Hi, 

I have used top and here are the results.

I don't have a lot running but to be frank, this does not mean a great deal to me.

Drew


top - 14:36:48 up 6 min,  2 users,  load average: 0.72, 1.31, 0.76
Tasks: 151 total,   2 running, 149 sleeping,   0 stopped,   0 zombie
Cpu(s): 10.2%us,  1.8%sy,  0.0%ni, 88.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2053320k total,  2001256k used,    52064k free,    11548k buffers
Swap:   489940k total,    82644k used,   407296k free,   110952k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                 
 2439 drew      20   0 37104  12m 9636 S   18  0.6   0:03.50 gnome-terminal                          
 1253 root      20   0 37328 8608 5524 S    5  0.4   0:19.34 Xorg                                    
 2175 drew      20   0 63116  18m 7264 S    2  0.9   0:08.62 compiz.real                             
 2458 drew      20   0  2472 1188  884 R    1  0.1   0:00.45 top                                     
    1 root      20   0  2532  644  644 S    0  0.0   0:01.58 init                                    
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                             
    4 root      15  -5     0    0    0 S    0  0.0   0:00.01 ksoftirqd/0                             
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                              
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.01 migration/1                             
    7 root      15  -5     0    0    0 S    0  0.0   0:00.01 ksoftirqd/1                             
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                              
    9 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0                                
   10 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/1                                
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 cpuset                                  
   12 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                 
   13 root      15  -5     0    0    0 S    0  0.0   0:00.00 netns                                   
   14 root      15  -5     0    0    0 S    0  0.0   0:00.00 async/mgr                               
   15 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0                           
   16 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1                           
   17 root      15  -5     0    0    0 S    0  0.0   0:00.06 kblockd/0                               
   18 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1                               
   19 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                  
   20 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                            
   21 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_hotplug                           
   22 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/0                                   
   23 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/1                                   
   24 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux

---

### Post by akashiraffee on 2010-02-15
If I were you I would subscribe to the Evolution user mailing list (look on their homepage), I know they have one.

Usually a developer is available on the mailing lists and they have some motivation to see their software working.  Otherwise you will just be waiting here forever.

**I very much doubt you are actually running out of memory.**  This is some bug whereby they are reading a NULL pointer and assuming it was from an allocation failure, when in fact by default the linux kernel never does that (fails to allocate, even when out of memory).  So there is some other reason the pointer ended up NULL and they failed to account for this.

---

### Post by Cabs21 on 2010-02-15
get a spork.deb file to fix it. ;)

---

### Post by gmargo on 2010-02-15
> **drew boardman said:**
> 
I have 501MB swap partition.  It use to work fine.
I do not understand the part "Keep a window open with top running".
Whats top?

500MB swap is small for a busy 2GB system.  For a relatively idle system it will work fine.  Consider: All of the running programs (including the windowing system) allocate memory and stack space, and all of that allocated memory must fit within RAM+swap.

The general rule of thumb on swap used to be 2x to 2.5x the size of RAM.  If you google for "sizing swap" or "swap size" you'll see these days "they" are recommending RAM+2GB for swap.  Anyway I think you should have at least 2GB.  Personally I use 4GB swap on my 1GB RAM system.

If you open a terminal window and run the "**top**" command (read about **top** in the **top(1)** man page) you'll be able to see current memory and swap usage.  If you hit a ">" key, then the sort shifts one column over to the %MEM field and that will really show who is sucking up the memory.  There are also graphical equivalents to **top**.  Such as ... the Gnome System Monitor (menu: System->Administration->System Monitor)

If you are interested in increasing the size of your swap space, you could repartition your disk if it's convenient.  Alternatively, the no-repartition solution is to create a file in the filesystem, and tell the system to use that file for additional swap space.  (Alternatively #2, you could avoid memory hogging programs.:p)

Just curious: are you running your EEE PC 901 with a small SSD drive or do you have some hard disk space to work with?

-------------------------------------------------------
Just saw your message about top output.....

```

top - 14:36:48 [COLOR=Red]up 6 min[/COLOR],  2 users,  load average: 0.72, 1.31, 0.76
Tasks: 151 total,   2 running, 149 sleeping,   0 stopped,   0 zombie
Cpu(s): 10.2%us,  1.8%sy,  0.0%ni, 88.0%id,  0.0%wa,  0.0%hi,  0.0%si,   0.0%st
[COLOR=Red]Mem:   2053320k total,  2001256k used[/COLOR],    52064k free,    11548k buffers
[COLOR=Red]Swap:   489940k total,    82644k used[/COLOR],   407296k free,   110952k cached

```Looks to me like you've just rebooted, and already all of your memory is in use (although some is in disk buffers) and you've spilled over into swap.  Now start doing your normal stuff and keep and eye on the swap usage.

Here's an interesting comparison.  The following is a "top" header from a Karmic instance running in a virtual machine with only 384MB memory.  It is running the Gnome desktop, newly booted and logged in.  However, it is _not_ running **compiz**.  Notice how the memory is used but the swap is barely touched.

```

top - 06:11:51 up 42 min,  3 users,  load average: 0.00, 0.08, 0.16
Tasks: 133 total,   1 running, 132 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.4%us,  4.0%sy,  5.1%ni, 80.8%id,  7.7%wa,  0.1%hi,  0.1%si,  0.0%st
[COLOR=Red]Mem:    379928k total,   366556k used[/COLOR],    13372k free,    71924k buffers
[COLOR=Red]Swap:  1461872k total,     3000k used[/COLOR],  1458872k free,   171368k cached

```

---

### Post by akashiraffee on 2010-02-15
@gmargo: Good eye.

That is a** ridiculously huge chunk of memory to have consumed at start-up **and it is not simply compiz.  I run 2gb and with compiz it is still under half a gb after boot.

I would start top, press captial O to select sort order, then choose "n" to pick %MEM as the sort criteria (right now you have it on %CPU).  This will list the processes by memory usage -- if the ones at the top say 0, press R to reverse the order (highest to lowest).

Still, in any case there is still enough memory left and I will bet adding swap will not make any difference to the problem, but you could try.  

But memory problems generally do not manifest themselves this way.

---

### Post by drew boardman on 2010-02-15
Dear All,

Here is the result with O
 ____________________
< You'll be sorry... >
 --------------------
  \
   \
       ___  
     {~._.~}
      ( Y )
     ()~*~()   
     (_)-(_)   
drew@drew-laptop ~ $ top

top - 16:45:40 up  2:15,  2 users,  load average: 0.35, 0.70, 0.42
Tasks: 154 total,   1 running, 150 sleeping,   2 stopped,   1 zombie
Cpu(s):  0.8%us,  1.1%sy,  0.0%ni, 97.9%id,  0.0%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   2053320k total,   975892k used,  1077428k free,    30324k buffers
Swap:   489940k total,    16124k used,   473816k free,   441388k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4889 root      20   0 32584  12m 7132 S    1  0.6   0:14.50 Xorg               
 5272 drew      20   0  237m  61m  23m S    1  3.1   0:29.58 firefox            
top - 16:47:54 up  2:17,  2 users,  load average: 0.22, 0.51, 0.38
Tasks: 154 total,   2 running, 149 sleeping,   2 stopped,   1 zombie
Cpu(s):  5.1%us,  2.1%sy,  0.0%ni, 92.6%id,  0.0%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   2053320k total,   986272k used,  1067048k free,    30396k buffers
Swap:   489940k total,    16124k used,   473816k free,   450780k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                            
 5272 drew      20   0  237m  61m  23m S    1  3.1   0:31.36 firefox                                            
 5068 drew      20   0  100m  11m 8304 S    0  0.6   0:01.01 gnome-settings-                                    
 5286 drew      20   0 94536 9524 6616 S    0  0.5   0:00.28 evolution-data-                                    
 5053 drew      20   0 94012 4436 3364 S    0  0.2   0:00.43 pulseaudio                                         
 5196 drew      20   0 93580 7840 6284 S    0  0.4   0:00.24 gnome-power-man                                    
 5192 drew      20   0 93460  10m 8180 S    0  0.5   0:00.52 gnome-volume-co                                    
 5175 drew      20   0 84660  26m  15m S    0  1.3   0:03.09 nautilus                                           
 2175 drew      20   0 80932  16m 4084 T    0  0.8   1:07.85 compiz.real                                        
 5173 drew      20   0 67740  24m 8872 S    2  1.2   0:05.96 compiz.real                                        
 5198 drew      20   0 67576  11m 9164 S    0  0.6   0:00.28 evolution-alarm                                    
 5185 drew      20   0 59840  30m  15m S    0  1.5   0:08.57 mintmenu                                           
 5201 drew      20   0 56236  20m  11m S    0  1.0   0:01.26 mintUpdate                                         
 4988 drew      20   0 40712 3492 2840 S    0  0.2   0:00.04 gnome-keyring-d                                    
 5177 drew      20   0 40624 3444 2636 S    0  0.2   0:00.19 bonobo-activati                                    
 5249 drew      20   0 40376 3256 2620 S    0  0.2   0:00.38 gvfs-gdu-volume                                    
 5174 drew      20   0 38916  15m  11m S    0  0.8   0:01.85 gnome-panel                                        
 5376 drew      20   0 37432  12m 9648 S    6  0.6   0:02.63 gnome-terminal                                     
  729 syslog    20   0 34828  892  632 S    0  0.0   0:00.28 rsyslogd                                           
 4889 root      20   0 33016  12m 7332 S    6  0.6   0:18.38 Xorg                                               
 5194 drew      20   0 31712  11m 8792 S    0  0.6   0:00.75 nm-applet                                          
 5079 drew      20   0 29796 2456 1956 S    0  0.1   0:00.01 gvfs-fuse-daemo                                    
 5189 drew      20   0 29532  14m 8200 S    0  0.7   0:00.52 python                                             
 5098 drew      20   0 27120  11m 8416 S    0  0.6   0:01.67 notify-osd                                         
 5003 drew      20   0 25508 6644 5276 S    0  0.3   0:00.25 gnome-session                                      
 5202 drew      20   0 22912 8696 6452 S    0  0.4   0:00.42 bluetooth-apple                                    
 5070 drew      20   0 22456 7356 5324 S    0  0.4   0:00.26 seahorse-daemon                                    
 1080 root      20   0 20504 2232 1852 S    0  0.1   0:00.26 console-kit-dae                                    
 5223 drew      20   0 19764 9328 7520 S    0  0.5   0:00.40 gtk-window-deco                                    
 1086 root      20   0 18676 2612 2120 S    0  0.1   0:01.47 NetworkManager                                     
 5209 drew      20   0 17940 2936 1564 S    0  0.1   0:00.02 gnome-screensav                                    
 5200 drew      20   0 17256 6552 5188 S    0  0.3   0:00.20 gdu-notificatio                                    
 5191 drew      20   0 16656 5708 4600 S    0  0.3   0:00.11 polkit-gnome-au

---

### Post by drew boardman on 2010-02-15
Sorry, I forgot to reply to all the questions.

Its a 20Gb SSD machine (4+16)
4Gb is \home
16Gb is extended with 501Mb as swap and the rest as \
I use an 8Gb flash card when I need extra space and when using at home I use a 1Tb external HDD.

Thanks for the advice.

Drew

---

### Post by drew boardman on 2010-02-23
Thanks everybody for their help.

The problem has been solved, it seems, by increasing the swap size up to 2gb.

It would seem to be a memory problem after all.

Drew

---

