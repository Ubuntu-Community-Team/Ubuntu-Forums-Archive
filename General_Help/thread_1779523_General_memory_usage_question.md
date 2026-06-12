---
title: "General memory usage question"
date: 2011-06-10
forum: General Help
---

### Post by ratcheer on 2011-06-10
I just got a new PC with 8 GB RAM. My old PC had 1 GB and, when I was running Unity, Firefox, and a couple of small apps (KeePass and a terminal), it would often use all the RAM and just a little swap space. It usually din't even need to use the swap space.

Now, I just noticed that my new PC is using 1.8 GB of RAM. I am running the classic Gnome 2 panel desktop, Firefox with one tab open, KeePass, and a terminal. No swap is being used, but it is blowing me away that so much RAM is being consumed when my old PC did the same stuff with so much less memory.

Is this normal?

Tim

PS - Firefox is using 919 MB all by itself.

---

### Post by papibe on 2011-06-10
Both are 32bit versions? If the new one uses 64bit, that could be an explanation.

Regards.

---

### Post by mc4man on 2011-06-10
What does something like this show?
ps aux |grep firefox

---

### Post by ratcheer on 2011-06-10
> **papibe said:**
> Both are 32bit versions? If the new one uses 64bit, that could be an explanation.

Regards.

Could be. The old one was 32-bit, the new one is 64. I don't see any overt reason why that should cause higher memory usage, though. Maybe slightly higher, but this is about double.

Thanks,
Tim

---

### Post by ratcheer on 2011-06-10
> **mc4man said:**
> What does something like this show?
ps aux |grep firefox

tim       4788  6.4  1.8 803404 147364 ?       Sl   16:15   0:44 /usr/lib/firefox-4.0.1/firefox-bin

Tim

---

### Post by hakermania on 2011-06-10
Maybe tasks take as Memory as not to fill it, and if a lot of memory is available then they consume the most so as to run at best perforrmance?

---

### Post by mc4man on 2011-06-10
> tim 4788 6.4 [COLOR="MediumTurquoise"]1.8[/COLOR] 803404 [COLOR="Blue"]147364[/COLOR] 
The blue is all that really counts (RSS mem  = used, light blue is %
Overall the more memory 'in use'  is generally a good thing, apps should open and respond quicker.

Edit: the 147MB used is a little higher than I see, though ok. FF tends to go up and down a bit, I start at around 65MB and range between there and 125 normally.

A more extreme ex. would be to open all of those "Latest Headlines" from BBC  at once in tabs, I'd see this after they all loaded
> doug      4522 67.7 22.9 1125916 [COLOR="Blue"]709160[/COLOR] ?      Sl   17:52   1:36 /usr/lib/firefox-4.0.1/firefox-bin
doug      4608 53.1  8.7 907960 [COLOR="Blue"]269676[/COLOR] ?       Rl   17:53   0:55 /usr/lib/firefox-4.0.1/plugin-container /home/doug/.mozilla/plugins/libflashplayer.so -omnijar /usr/lib/firefox-4.0.1/omni.jar 4522 true plugin

Then after closing and reopening (the flash plugin has a habit of not releasing mem till FF restarts
doug      4846  6.4  3.3 462296 [COLOR="Blue"]104668[/COLOR] ?       Sl   17:56   0:32 /usr/lib/firefox-4.0.1/firefox-bin

---

### Post by ratcheer on 2011-06-10
Here is what I see in top:

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                
 4256 root      20   0  [COLOR=Red]351m[/COLOR]  77m  56m S    1  1.0   2:45.82 Xorg                                                   
 4413 tim       20   0  [COLOR=Red]642m[/COLOR] 113m  37m S    1  1.4   1:53.36 compiz                                                 
 4597 tim       20   0  [COLOR=Red]321m[/COLOR]  16m  11m S    0  0.2   0:00.78 gnome-terminal                                         
 4788 tim       20   0  [COLOR=Red]835m[/COLOR] 178m  37m S    0  2.2   2:29.11 firefox-bin                                            
 5034 tim       20   0 92356  18m  12m S    0  0.2   0:06.88 npviewer.bin                                           
 5166 tim       20   0 19352 1356  968 R    0  0.0   0:00.03 top                                                    
    1 root      20   0 24088 2184 1332 S    0  0.0   0:01.04 init                    

I wish things would line up properly when I cut and paste. Sorry.

I am in Unity, now. Free currently shows 1911440 used, total.

Tim

---

### Post by ratcheer on 2011-06-10
I am not really worried about this, I am just curious. Also, I am wondering how my little old computer got by so well. If it was choked for memory, it didn't act like it and, like I said, it only occasionally used small amounts of swap space.

If y'all are wondering why I have even noticed this, it is because I had a 34 year IT career as a database administrator, and I just have old habits of keeping an eye on system resources.

Thanks,
Tim

---

### Post by JKyleOKC on 2011-06-10
> **ratcheer said:**
> Here is what I see in top:

  ```
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                
 4256 root      20   0  [COLOR=Red]351m[/COLOR]  77m  56m S    1  1.0   2:45.82 Xorg                                                   
 4413 tim       20   0  [COLOR=Red]642m[/COLOR] 113m  37m S    1  1.4   1:53.36 compiz                                                 
 4597 tim       20   0  [COLOR=Red]321m[/COLOR]  16m  11m S    0  0.2   0:00.78 gnome-terminal                                         
 4788 tim       20   0  [COLOR=Red]835m[/COLOR] 178m  37m S    0  2.2   2:29.11 firefox-bin                                            
 5034 tim       20   0 92356  18m  12m S    0  0.2   0:06.88 npviewer.bin                                           
 5166 tim       20   0 19352 1356  968 R    0  0.0   0:00.03 top                                                    
    1 root      20   0 24088 2184 1332 S    0  0.0   0:01.04 init
```                    

I wish things would line up properly when I cut and paste. Sorry.You mean like they do now? The trick is to highlight them, then click the "#" icon on the message-dialog toolbar to enclose them in "code" tags...

EDIT: Incidentally, the key column to look at in a "top" display is the one headed "%MEM" which shows how much of your memory is actually in use. If you sort on this column, you can be sure that it's all showing up.

Linux uses lots of otherwise-unused RAM as cache, since unused memory is just wasted. This causes the various reporting tools to report different and often conflicting values!

---

### Post by mc4man on 2011-06-10
The virt is not all that important, to some extent the higher the better, the RES is what the process has 'taken'.
If you run free -m it should be a bit clearer.
Ex. here now

```
free -m
             total       [COLOR="Blue"]used [/COLOR]      [COLOR="Blue"]free[/COLOR]     shared    buffers     cached
Mem:          3021       1229       1791          0        107        657
-/+ buffers/cache:        [COLOR="Blue"]465 [/COLOR]      [COLOR="Blue"]2556[/COLOR]
Swap:          106          0        106
```

---

### Post by ratcheer on 2011-06-10
```
free -m
             total       used       free     shared    buffers     cached
Mem:          7984       1927       6056          0        115        866
-/+ buffers/cache:        945       7039
Swap:         8581          0       8581

```That is still saying 1.9 GB used. Which is what I was asking about.

Thanks,
Tim

---

### Post by JKyleOKC on 2011-06-11
> **ratcheer said:**
> ```
free -m
             total       used       free     shared    buffers     cached
Mem:          7984       1927       6056          0        115        866
-/+ buffers/cache:        [COLOR="Red"]945[/COLOR]       7039
Swap:         8581          0       8581

```That is still saying 1.9 GB used. Which is what I was asking about.

Thanks,
TimNope, the 1927 figure includes almost a gigabyte being used as cache. Only the 945 MB I've made red is actually in use by programs. That's still a lot, but Firefox is notorious for expanding to keep all the RAM it can get...

---

### Post by ratcheer on 2011-06-11
Ok, thanks everyone!

Tim

---

