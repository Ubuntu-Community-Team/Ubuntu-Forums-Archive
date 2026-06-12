---
title: "CPU usage"
date: 2010-12-18
forum: General Help
---

### Post by Herasi on 2010-12-18
Hi. I'm not particularly Linux-savvy so bare with me; I noticed my laptop was a bit sluggish, and Ubuntu (10.04) was running slower than usual. I ran top, and this is what I got:
 ```
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 3518 root      20   0 26960 5956 2368 R 40.5  0.3 153:42.96 backend            
 3635 nc20user  20   0  757m 162m  32m R 30.2  9.3  46:47.58 firefox-bin       
  840 root      20   0  431m  83m  11m S  8.0  4.7  15:44.16 Xorg               
28313 nc20user  20   0 92244  30m  14m S  5.1  1.7   0:37.98 npviewer.bin       
 3220 nc20user  20   0 76064  22m  13m S  3.9  1.3  11:24.32 npviewer.bin       
28496 nc20user  20   0  209m  14m  10m S  3.5  0.9   0:01.69 gnome-terminal     
 1267 nc20user  20   0  262m  20m  13m S  1.6  1.2   3:38.27 gnome-panel        
 1271 nc20user  20   0  396m  21m  15m S  1.3  1.2   2:41.59 nautilus           
 1251 nc20user  20   0  302m  10m 7780 S  1.0  0.6   2:19.18 gnome-settings-    
28515 nc20user  20   0 19224 1400 1028 R  1.0  0.1   0:00.15 top                
  722 root      20   0 76592 3452 2760 S  0.6  0.2   1:19.94 gdm-binary         
 1272 nc20user  20   0  302m  16m  10m S  0.6  0.9   1:14.93 metacity           
 1344 nc20user  20   0  140m 5648 4420 S  0.6  0.3   1:53.37 indicator-me-se    
    1 root      20   0 23708 1924 1252 S  0.0  0.1   0:00.59 init               
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.01 kthreadd           
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S  0.0  0.0   0:00.09 ksoftirqd/0
```

I bolded the ones that bothered me the most. Why is this root taking up 40% of my CPU, and why will top not let me kill it? I have 2 GB of ram (Samsung NC20 notebook), that should be plenty to run Linux on. 

Any help would be much appreciated.

---

### Post by ajgreeny on 2010-12-18
I have no idea what this backend executable might be, the only one I can find on my system is **/usr/lib/cups/backend**, but that's a directory, so can't be the program, and ```
which backend 
```shows no output.

have a look on your system with ```
which backend
```and you may get some clues.

---

### Post by Herasi on 2010-12-18
'which backend' did nothing, it just went to a new line and waited for another command.

edit: Also, when firefox stops taking up so much CPU, the root increases even more (to ~88%)

---

### Post by ghost25 on 2010-12-18
Howdy. I'm having a bit of the same problem, running 10.04 on my desktop with older hardware.

As far as what "root" is, unless I'm mistaken, that's the admin section of Linux, which is kinda essential. If you kill root, you aren't gonna be able to accomplish much of anything, if that.

Like I said though, I'm experiencing more or less the same thing. I'm using Chrome as my browser, but up until maybe a week or two ago I had no problems. Right now, running Pidgin with one conversation window open, Chrome, Rhythmbox, and a Terminal, I'm averaging ~30% but if I try to do anything (open a new tab, switch focused window, whatever) it jumps to 100% CPU usage... this is rather concerning.

I never thought I'd ask this, but is there a way to scan for viruses in Ubuntu? I'm almost positive I'm clean, but that seems to be the only explanation I can come up with. I've updated what's needed to have been done, off a restart, but I still have much too high CPU usage.

Oh, FWIW my Ubuntu box is always on as it's my household music server, as well as my printing hub, so I kinda need it to be working. Also, I'm using this for school, so software failure is a can of worms I'd like best to avoid.

Sorry to hijack your thread... but my problems seem similar enough, I figure maybe we can both get some help.

---

### Post by ajgreeny on 2010-12-19
The root you talk of is simply the owner of the process **backend** that is running and taking so much cpu power.  The problem is in knowing what **backend** really is, and how come there is apparently no executable for it, but it is still running.

I don't think I have any more ideas, I'm afraid.

---

### Post by Herasi on 2010-12-20
Bump--lets see if anybody else has some input. xP Thanks for the responses.

---

### Post by mastablasta on 2010-12-20
Have a look here, maybe it will help: [http://ubuntuforums.org/showthread.php?t=1519431](http://ubuntuforums.org/showthread.php?t=1519431)

---

