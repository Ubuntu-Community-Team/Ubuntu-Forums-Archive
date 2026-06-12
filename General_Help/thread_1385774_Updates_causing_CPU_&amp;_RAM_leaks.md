---
title: "Updates causing CPU &amp; RAM leaks?"
date: 2010-01-19
forum: General Help
---

### Post by warfacegod on 2010-01-19
Has Update Manager been compromised? Last week I got an update for Transmission even though I remove Transmission 3 months ago. I've seen a few threads about that as well. Now today, I get an update for a xserver-intell-videodriver or something along those lines when I have nVidia graphics. Over the last few hours I've been watching my RAM use climb. As well as my CPU time is higher than average.

In an idle state, with Compiz running, CPU time 5 - 7% and RAM use is 200 - 225 MB

Normal use, with Compiz, consists of Amarok 1.4, and Firefox with one or maybe two tabs, and often Ktorrent with the CPU at around 15 - 17% and RAM use around 285 - 300 MB.

Instead, with normal use, CPU time is 30 - 70% and RAM use is 760 MB climbing slowly.

---

### Post by warfacegod on 2010-01-20
I just shut down all the apps and CPU time stayed about the same. RAM use dropped 160 MB to 600 MB which is roughly how much I would expect it to go down. However, 600 MB is still about 3X higher than it should be.

---

### Post by warfacegod on 2010-01-20
An interesting twist. top and System Monitor are all reporting the same over all amount of RAM being used but top is reporting *lower* amounts for each individual process.


Examples:        top              S.M.

swiftfox-bin     41 MB            57 MB

xorg             45 MB            90 MB

---

### Post by warfacegod on 2010-01-20
Now I'm baffled. I shutting down for several hours and now my system has been back up for 2 hours. System Monitor is now reporting 230 MB used RAM and top reports 740 MB.

---

### Post by gradinaruvasile on 2010-01-20
System monitor always reports less. I dunno exactly the reporting mechanisms but there are memory parts that are shared among processes etc. 
I use top and look at the %RES (resident size). 
Ad the memory doesnt has to be empty. In Linux the memory menegement is different than in Windows, it uses free memory for caching'n'stuff. But that memory is freed when needed. 

Memory usage sometimes climbs because of the browser - showing some flash ads can greatly increase the %CPU used.

I constantly have reported memory size (used) about 1-1.5 GB from 2 GB RAM (running Chromium with some tabs open, Skype, Sip Communicator, Seamonkey Mail, Compiz, some terminals, OpenOffice, sometimes VirtualBox too) and the system never slows down because of full memory. 

The intel driver update is normal, that package is part of the system's base opensource driver package installed by default.

---

### Post by warfacegod on 2010-01-20
> System monitor always reports less. I dunno exactly the reporting mechanisms but there are memory parts that are shared among processes etc.
I use top and look at the %RES (resident size).
Ad the memory doesnt has to be empty. In Linux the memory menegement is different than in Windows, it uses free memory for caching'n'stuff. But that memory is freed when needed.

Memory usage sometimes climbs because of the browser - showing some flash ads can greatly increase the %CPU used.

Thanks for the reply. It feels strange that I'm getting help as opposed to giving it. I know that my memory doesn't have to be empty, it just usually is. A threefold increase in RAM use from one day to the next is simply not normal. I know System Monitor doesn't report RAM as cache and didn't include the cache sizes in my calculations. Last night top and S.M. were reporting the same amount of used RAM (ignoring cache), this morning they are not. top is reporting over 500 MB more RAM use not including the cache.

Flash content is almost nonexistent in my Swiftfox setup. My system isn't slowing down either but I do want to know where my RAM has decided to go all of a sudden. I think I'm more concerned about a breach than the actual usage. I figure it would be easiest to find a breach (if any) by following the RAM.

So the Intel driver is normal. That's pretty much what I expected but I wasn't certain. That doesn't mean one of the other updates isn't responsible for this. I find hard to believe, although not impossible, that this issue and the updates aren't related somehow, considering this started happening a few hours after my last update.

---

### Post by lachild on 2010-01-20
This might be a bit off topic, but I too have been having issues after the last round of updates.

For me, my two systems are completely locking up at random.  The two machines are completely different with different everything (one AMD one Intel, one 32 bit one 64 bit, etc) so I don't think this is a hardware related issue.

I'm wondering if my issues are related to what you're seeing on your end?

LaChild

---

### Post by warfacegod on 2010-01-20
> **lachild said:**
> This might be a bit off topic, but I too have been having issues after the last round of updates.

For me, my two systems are completely locking up at random.  The two machines are completely different with different everything (one AMD one Intel, one 32 bit one 64 bit, etc) so I don't think this is a hardware related issue.

I'm wondering if my issues are related to what you're seeing on your end?

LaChild

It's quite possible. Cannonical doesn't seem to have done as good a job with updating this month. The last round of updates also fragged allot of Wubi installs. I spent a day almost exclusively helping the Wubi guys get Ubuntu back up. Some still haven't. If you like, follow this thread. you might find a solution to what is plaguing you.

---

### Post by warfacegod on 2010-01-23
I'm going to mark this as solved. I've been watching closely over the last few days and everything seems to be back to normal. I guess it was just a matter of waiting it out. Sort of like being up a tree with a 600 lbs. tiger below you. Either the tiger gets hungry enough to go looking for something else to eat or you fall asleep and fall out of the tree. Either way, the tiger gets lunch.

---

### Post by colinjones on 2010-01-24
warfacegod - I'm not so sure... I have seen a few threads with people talking about memory issues... I was looking because I am having similar issues.

Under "normal" load my system seems progressively to get slower and slower, and I can hear the HDD getting thrashed more and more. Yesterday it ground almost to a halt. 

I've seen in other threads recent mention that immediately after a reboot RAM useage being higher than it should be. Most seemed to be expecting in 200MB range but were getting 600+MB (yes, obviously I'm talking about physical memory and excluding cache and buffers)

I am also seeing around 610MB when I have first started (realistically only Cairo-dock is running at that point, but its usage is pretty low) on a 2GB system with 6GB swap. At this point swap isn't being used at all, of course.

Over time this seems to climb slowly, even when I close my apps. The problem seems to start occurring when memory is getting quite full, and swap starts being used.. the amount of memory being used seems far more than it should... realistically for my purposes I should rarely be using swap at all, and yet I see it climb up into many hundreds of MB! I'm assuming this is the performance issue, as the HDD spends its entire time swapping.

But the underlying issue is how much memory is being consumed. If I look at top and sort by RES, the RES values seem to match the "Memory" values in SM very accurately (except firefox, there are a few 10's of MB difference, but not much) and both report the same amount of total RAM being used as free -m

The crunch seems to be that adding up all the RES's or all the Memory's for all processes falls far short of the total amount of memory consumed being reported by all these tools. It just seems to have disappeared, and I have read a couple of other recent threads reporting the same thing.

Seems like a memory leak but into a blackhole! And that would certainly cause performance issues over time.

There are only 2 other pieces of information I can add right now, they may be completely unrelated, but...
1. console-kit-dae is consuming ~200MB of memory, I don't see how that could possibly be necessary for that process (I suspect that it was much lower immediately after reboot, and will need to check that)
2. the virtual memory allocations to many processes are truly huge! eg firefox - 744MB, cairo-dock - 588MB, Nautilus - 573MB, Rythmbox - 566MB, etc. Don't know if this is normal (using 64 bit), or even important.

EDIT: I noticed that there is at least 1 known memory leak in consolekit, fixed subsequent to the Karmic release, so that is probably unrelated to the main issue.

---

### Post by warfacegod on 2010-01-24
Perhaps I marked this as solved too soon. My RAM is up around 700 MB again. Altiugh my CPU is still behaving itself. I'd seen several threads on this as well, colinjones, but when I scanned through them they seemed to related to the graphics driver. I ignored them because I hadn't change my graphics driver. I may have been mistaken in that assumption.

---

### Post by llawwehttam on 2010-01-24
> **lachild said:**
> This might be a bit off topic, but I too have been having issues after the last round of updates.

For me, my two systems are completely locking up at random.  The two machines are completely different with different everything (one AMD one Intel, one 32 bit one 64 bit, etc) so I don't think this is a hardware related issue.

I'm wondering if my issues are related to what you're seeing on your end?

LaChild

I have had similar issues after recent updates.

---

### Post by ibuclaw on 2010-01-24
I would like to see some figures, personally. :)

```
free -m
```

```
top -d10 -n1
```


Also, does:
```
sync; sudo bash -c 'echo 3>/proc/sys/vm/drop_caches'
```
Reduce this memory?

Regards
Iain

---

### Post by warfacegod on 2010-01-24
free -m
```
warfacegod@warfacegod-laptop:~$ top

top - 17:29:45 up 21:20,  2 users,  load average: 0.03, 0.05, 0.03
Tasks: 154 total,   1 running, 153 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.1%us,  4.4%sy,  0.0%ni, 88.3%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   2061252k total,  1103204k used,   958048k free,    29416k buffers
Swap:        0k total,        0k used,        0k free,   437032k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1490 root      20   0  136m  84m 8940 S   10  4.2  42:38.33 Xorg               
 3284 warfaceg  20   0 24840  10m 8268 S    6  0.5  79:01.96 multiload-apple    
25575 warfaceg  20   0  336m 111m  40m S    3  5.5   5:25.53 swiftfox-bin       
 2825 warfaceg  20   0 48036  20m 9.9m S    2  1.0   4:02.64 gnome-panel        
 2820 warfaceg  20   0 27888  12m 8276 S    2  0.6   8:55.04 metacity           
 1309 root      20   0 19768 3112 2324 S    0  0.2   0:05.07 NetworkManager     
23417 warfaceg  20   0  246m  72m  18m S    0  3.6  26:07.30 amarokapp          
    1 root      20   0  2648 1416 1012 S    0  0.1   0:01.35 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.02 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:30.08 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.86 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.77 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.06 events/1           
warfacegod@warfacegod-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2012       1076        935          0         28        426
-/+ buffers/cache:        621       1391
Swap:            0          0          0

```

top -d10 -n1
```
top - 17:32:17 up 21:23,  2 users,  load average: 0.00, 0.03, 0.02
Tasks: 154 total,   1 running, 153 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.5%us,  4.4%sy,  0.0%ni, 87.0%id,  1.2%wa,  0.2%hi,  0.7%si,  0.0%st
Mem:   2061252k total,  1102932k used,   958320k free,    29616k buffers
Swap:        0k total,        0k used,        0k free,   437048k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3284 warfaceg  20   0 24840  10m 8268 S    8  0.5  79:09.84 multiload-apple    
 1490 root      20   0  136m  84m 8940 S    4  4.2  42:43.65 Xorg               
22578 warfaceg  20   0 36996  12m 9736 S    2  0.6   0:00.80 gnome-terminal     
    1 root      20   0  2648 1416 1012 S    0  0.1   0:01.35 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.02 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:30.14 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.86 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.77 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.06 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 cpuset             
   12 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   13 root      15  -5     0    0    0 S    0  0.0   0:00.00 netns              
   14 root      15  -5     0    0    0 S    0  0.0   0:00.00 async/mgr   
```

free -m after using: sync; sudo bash -c 'echo 3>/proc/sys/vm/drop_caches'
```
warfacegod@warfacegod-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2012       1079        933          0         29        428
-/+ buffers/cache:        621       1391
Swap:            0          0          0

```

Notice my cache actually went up 1 MB.

---

### Post by ibuclaw on 2010-01-24
Hmm, to be honest, I really don't see an issue here. Linux utilises RAM by default. So it is natural to see it increase over time. The longer the uptime, the more it will use as cache.

See this example:
```

[~] free -m
             total       used       free     shared    buffers     cached
Mem:          2016       1955         61          0        205       1395
-/+ buffers/cache:        354       1662
Swap:         3623          0       3623

```

If the above was your system, would you worry about it?

Regards
Iain

---

### Post by warfacegod on 2010-01-24
Not especially, because the majority of RAM use is cache. Also bearing in mind that I'm not familar with that system, what it's normal use should be, or how long it's been on.

free -m about 25 minutes after my last post
```
warfacegod@warfacegod-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2012       1310        702          0         34        623
-/+ buffers/cache:        652       1360
Swap:            0          0          0

```

I'm concerned about this because it is not normal behavior for my system. The usage is considerably higher than is normal for my system. RAM use also rarely fluctuates more than a 10 MB for days. Now it's climbing steadily over the course of minutes and hours and I'm not counting RAM as cache either. This is actual RAM use only that I've been watching.

---

### Post by danastasio on 2010-01-24
I was having the same problems in Karmic and Lucid 1 + 2. Figuring I was out of options, I used the default NVidia installer from the nvidia website, and that seemed to solve my problems O.o

---

### Post by warfacegod on 2010-01-24
> **danastasio said:**
> I was having the same problems in Karmic and Lucid 1 + 2. Figuring I was out of options, I used the default NVidia installer from the nvidia website, and that seemed to solve my problems O.o

I'm using the 173 driver, the same one I've used since I got my laptop several years ago. Why would it start leaking RAM now?

---

### Post by colinjones on 2010-01-24
I'm using 185 of the nVidia driver. But I haven't seen anything so far that points towards the video subsystem specifically...

tinivole - please read through the thread. we were all pretty clear that we were NOT talking about cache/buffers, this is real RAM usage supposedly by processes.... and that's my main point above.... the RAM being used, ie the first number after "-/+ buffers/cache" when issuing the free -m command, is much higher on my system than the total of all processes' RES values, and the gap keeps increasing...

warfacegod - can you please check your system after it has been running for some time and compare these 2 values? And also see if you can see if the difference is increasing? In other words, can you track down where that 652MB is, in your last free -m output?

---

### Post by warfacegod on 2010-01-24
> **colinjones said:**
> 
warfacegod - can you please check your system after it has been running for some time and compare these 2 values? And also see if you can see if the difference is increasing? In other words, can you track down where that 652MB is, in your last free -m output?

I just rebooted so I'll have to wait until tomorrow to post the results.

---

### Post by warfacegod on 2010-01-24
I just rebooted again to get a report of free -m right after bootup. I got a GRUB prompt with error: file not found. Obviously I'm not going to be able to find out what's going on with the RAM until I solve this. I can't help but think that they are related.

---

### Post by Leppie on 2010-01-25
> **warfacegod said:**
> I can't help but think that they are related.
i think you did so many nasty things to your system, it's now getting back at you... :P

---

### Post by audiomick on 2010-01-25
> **Leppie said:**
> i think you did so many nasty things to your system, it's now getting back at you... :P

What on earth gives you that idea?

---

### Post by Leppie on 2010-01-25
> **audiomick said:**
> What on earth gives you that idea?
dunno... some little bird told me a something something...

---

### Post by warfacegod on 2010-01-25
> **Leppie said:**
> dunno... some little bird told me a something something...

I blame the bird.

---

### Post by warfacegod on 2010-01-25
This is all behavior I was seeing in my normal install not my experiment partition.

---

### Post by audiomick on 2010-01-25
How do you know they don't talk to each other late at night when all is quiet?

---

### Post by Leppie on 2010-01-25
> **warfacegod said:**
> I blame the bird.
i would too if i were you... ;)

---

### Post by warfacegod on 2010-01-25
Some of the strange behaviors that my experiment install was showing did start to show in my normal install, but it stopped when I installed Mythbuntu into the experiment partition. It must have known what was coming and left nefarious instructions. I should have known they were plotting on me.

---

### Post by Leppie on 2010-01-25
> **warfacegod said:**
> Some of the strange behaviors that my experiment install was showing did start to show in my normal install, but it stopped when I installed Mythbuntu into the experiment partition. It must have known what was coming and left nefarious instructions. I should have known they were plotting on me.
of course they were... words spread fast... :P

---

### Post by warfacegod on 2010-01-25
Great! Now even my own laptop is involved in the New World Order.

---

### Post by Leppie on 2010-01-25
> **warfacegod said:**
> Great! Now even my own laptop is involved in the New World Order.
of course, it's nicer to be able to enslave a deity... :P

---

### Post by warfacegod on 2010-01-25
> **Leppie said:**
> of course, it's nicer to be able to enslave a deity... :P

I do not decree slavery for anyone. Except Martians. Pesky little critters.

---

### Post by colinjones on 2010-01-25
so back OT! any update?

---

### Post by warfacegod on 2010-01-25
> **colinjones said:**
> so back OT! any update?

Nope, my laptop is still down for the count. It is impossible to fix without access to another computer with a working USB port or I go back to my old school technique of data transfer using shaped explosives.

---

### Post by Leppie on 2010-01-25
> **warfacegod said:**
> Nope, my laptop is still down for the count. It is impossible to fix without access to another computer with a working USB port or I go back to my old school technique of data transfer using shaped explosives.
maybe some telepathy?

---

### Post by warfacegod on 2010-01-25
> **Leppie said:**
> maybe some telepathy?

I gave it a stern talking to. But, just like anyone with an attitude problem, it didn't want to hear it.

---

### Post by Leppie on 2010-01-25
> **warfacegod said:**
> I gave it a stern talking to. But, just like anyone with an attitude problem, it didn't want to hear it.
i suspect you're becoming a softy...

---

### Post by audiomick on 2010-01-25
> **Leppie said:**
> i suspect you're becoming a softy...

depends what he did the talking with. I find talking to things with a large hammer or a piece of four by two is often very effective...

---

### Post by Leppie on 2010-01-25
> **audiomick said:**
> depends what he did the talking with. I find talking to things with a large hammer or a piece of four by two is often very effective...
also effective for restoring things??? :P

---

### Post by warfacegod on 2010-01-25
It's right next to me and saw me type "shaped explosives". It didn't care. Jumper cables is next.

---

### Post by Leppie on 2010-01-25
> **warfacegod said:**
> It's right next to me and saw me type "shaped explosives". It didn't care. Jumper cables is next.
see, you have become a softie... threatening to do something, but then don't do it...

---

### Post by warfacegod on 2010-01-26
> **Leppie said:**
> see, you have become a softie... threatening to do something, but then don't do it...

I can be a forgiving god, but my divine wrath is quick to anger and swift to strike.

---

### Post by warfacegod on 2010-02-05
I've had my laptop running again for several days now. I updated and have left it on for that entire time. I have seen none of the behaviors that I was seeing before and I now seriously doubt that my RAM use and broken GRUB were related in anyway.

```
warfacegod@warfacegod-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2012        467       1544          0         36        197
-/+ buffers/cache:        234       1778
Swap:          564          0        564

```

As you can see, RAM use is at around 230 MB. Right about what mine should be.

---

### Post by audiomick on 2010-02-05
Just for interest sake, did you actually have to re-install, or just fix the grub? I don't think I read anything anywhere where you said...

---

### Post by warfacegod on 2010-02-05
All I *had* to do was reinstall GRUB. I chose to install UNR over my Mythbuntu install in my experiment partition. Sort of killing two birds with one stone. GRUB is not on either of my install partitions.

---

### Post by colinjones on 2010-02-05
can you do a top for mem and virt showing console-kit-daemon after at least 24hrs? It starts around 4MB, but for me it grows and grows! (409MB RAM at the mo!)

---

### Post by audiomick on 2010-02-05
And the usage figures you just quoted, are they in the new install in what was the experiment partition, or in the original main install? And have you shared any partitions between the two installs?

---

### Post by warfacegod on 2010-02-05
> **colinjones said:**
> can you do a top for mem and virt showing console-kit-daemon after at least 24hrs? It starts around 4MB, but for me it grows and grows! (409MB RAM at the mo!)

This is after 3? days.

---

### Post by warfacegod on 2010-02-05
> **audiomick said:**
> And the usage figures you just quoted, are they in the new install in what was the experiment partition, or in the original main install? And have you shared any partitions between the two installs?

Old install where I was seeing this RAM use in the first place (never bothered to check UNR or Mythbuntu). No partition sharing aside from my external.

sda1 is my main install. sda3 is the experiment install. My swap is off. The RAM use seemed to be independent of swap being on or off and my swapiness setting.

---

### Post by audiomick on 2010-02-05
> **warfacegod said:**
> I've had my laptop running again for several days now. **[COLOR=Red]I updated[/COLOR]** and have left it on for that entire time. I have seen none of the behaviors that I was seeing before ...
Maybe your earlier thought was right. Maybe you got something in an update that has since been fixed with a new update?? Your box was broken long enough for that to have happened, I think.

---

### Post by warfacegod on 2010-02-05
> **audiomick said:**
> Maybe your earlier thought was right. Maybe you got something in an update that has since been fixed with a new update?? Your box was broken long enough for that to have happened, I think.

That's what I figured. I should have said that before. I am ashamed. I nolonger deserve to live. I shall excorporate this incarnation.

---

### Post by audiomick on 2010-02-05
No need for that...
Did you see this
[http://ubuntuforums.org/showpost.php?p=8778397&postcount=6](http://ubuntuforums.org/showpost.php?p=8778397&postcount=6)
Who knows if it is related.

---

### Post by warfacegod on 2010-02-05
No, I hadn't. I've recommended others do that for boot and other issues but it never occurred to me to do it myself. If my normal install starts misbehaving again, I'll try it. I will, however, do it on my experiment install. (After I fix my truck...again.)

---

### Post by Leppie on 2010-02-05
what do you do to your equipment???
you run down your laptop with your truck? and then when you've repaired your laptop, you get some crazy algorithm to mess up your truck's engine's controlling system? :evil:

---

### Post by warfacegod on 2010-02-05
> **Leppie said:**
> what do you do to your equipment???
you run down your laptop with your truck? and then when you've repaired your laptop, you get some crazy algorithm to mess up your truck's engine's controlling system? :evil:

Fear not, it is all a part of the plan.:twisted:

WAAHAAAhaahhahahahhahaaaaa!

---

### Post by Leppie on 2010-02-05
> **warfacegod said:**
> Fear not, it is all a part of the plan.:twisted:

WAAHAAAhaahhahahahhahaaaaa!
well, hope it's working out for you... ;)

---

