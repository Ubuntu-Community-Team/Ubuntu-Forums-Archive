---
title: "Anyone know where my RAM is going?"
date: 2010-01-05
forum: General Help
---

### Post by danastasio on 2010-01-05
starting my system, my computer lists ~340 MB of RAM in use, which is a bit high IMHO, but after several hours of use, it creeps up and up, before I shutdown my computer, i usually close out of all my programs, and my computer usually reports upwards of 700 MB of RAM at this point! The ONLY thing that will be running is compiz and gnome-do. looking under system monitor, nothing is using more than ~30 MB of RAM. Does anyone have any idea where my RAM is going? or is this a mere reporting discrepency?:confused:

---

### Post by mocoloco on 2010-01-05
System > Administrator > System Montor.  Click on the "Memory" column to put in in descending order highest to lowest.

---

### Post by mcduck on 2010-01-05
> **danastasio said:**
> starting my system, my computer lists ~340 MB of RAM in use, which is a bit high IMHO, but after several hours of use, it creeps up and up, before I shutdown my computer, i usually close out of all my programs, and my computer usually reports upwards of 700 MB of RAM at this point! The ONLY thing that will be running is compiz and gnome-do. looking under system monitor, nothing is using more than ~30 MB of RAM. Does anyone have any idea where my RAM is going? or is this a mere reporting discrepency?:confused:

Are you sure you aren't just misunderstanding how the memory is used?

To check the actual memory usage I recommend opening a terminal and running "free -m". Then read from the "+/- buffers/cache"-line to see the amount of RAM used by programs, and the amount of RAM available for them.

Linux doesn't waste your RAM by leaving it unused, all memory that isn't used by running programs is used as cache for recenty used data to increase your system's performance. Since cached data is dropped if any program needs more RAM taht part of memory still counts as free from any program's point of view. But the point is that after the system has been running for a while all your RAM is *supposed to* be in some use, if not by programs then as disk cache.

---

### Post by jocko on 2010-01-05
To see the real memory usage, type "free -m" in a terminal. This is what I see:
```
jocko@jocko-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1508       1456         51          0         73        999
-/+ buffers/cache:        384       1123
Swap:         4996          1       4995
```
So I have only 51 Mb completely unused ram out of 1508 Mb total, but of the 1456 Mb ram that is being used, only 384 Mb is used by the operating system, xorg, gnome plus all my currently running programs and services. The rest is just cached files that have been used at some point since I booted my computer, that just take up space until they are either needed again or until they are overwritten with something else that is needed by a running program.

This is the way linux memory management is supposed to work. Since your hard drive is a LOT slower (1000-fold?) than your ram it makes a lot of sense to keep files in ram as long as possible just to save the time it takes to read them back from the hard drive the next time they are needed.

---

### Post by bodhi.zazen on 2010-01-05
> **mcduck said:**
> Are you sure you aren't just misunderstanding how the memory is used?

To check the actual memory usage I recommend opening a terminal and running "free -m". Then read from the "+/- buffers/cache"-line to see the amount of RAM used by programs, and the amount of RAM available for them.

Linux doesn't waste your RAM by leaving it unused, all memory that isn't used by running programs is used as cache for recenty used data to increase your system's performance. Since cached data is dropped if any program needs more RAM taht part of memory still counts as free from any program's point of view. But the point is that after the system has been running for a while all your RAM is *supposed to* be in some use, if not by programs then as disk cache.

To follow up on this most excellent post ...

Linux does not use ram the same way as Windows. See these links:

[http://www.cyberciti.biz/faq/linux-check-memory-usage/](http://www.cyberciti.biz/faq/linux-check-memory-usage/)

This one is fun to read

[http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage](http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage)

And for a more technical explanation :

[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html)

---

### Post by danastasio on 2010-01-05
Right, I understand caching and buffers and whatnot, but what i dont understand is that when my computer starts, it uses ~340 MB of RAM system wise, free -m AND system monitor applet both show this (11% in use by PROGRAMS), this is when nothing but gnome-do is running, so why, after i close every program after hours of use, free -m and sys applet both report ~1 GB in use by PROGRAMS and a whole lot more as cache. Is something being mistaken as a program thats actually cache? (i know that sounds impossible but -I- never know :P)

Thanks for the replies!

free -m

```
dave@dave-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3018       2367        651          0        173       1403
-/+ buffers/cache:        789       2228
Swap:         8911          0       8911

```

NOTE: im totally ignoring the "free" field, just the -/+ buffers/cache field is what im paying attention to.

So i guess my question really is: why are "programs" (not cache) using so much RAM when nothing is running.

---

### Post by mcduck on 2010-01-05
Then it must be some of the programs you have running. Try not using Gnome-Do, or whatever other programs, panel applets (or really anything else) you are using. Try disabling every piece of software that doesn't belong to the default setup, one by one, until you find the one that's using more memory than you'd like it to.

Or run "top" and check how much RAM your programs are using.

Remember, not only applications use memory and have bugs. Every single piece of software you run is the same, even if it's just some small background service, GTK theme engine or panel applet.

(Assuming that the situation is like you said, and Gnome-Do is the only extra app you have started after booting the system, that would pretty much mean that Gnome-Do is your problem.. But you'd still better actually check the memory usage with "top")

edit: also you should check that the programs you have closed are actually closed, and not just appear to be so. Even if the program's window disappears the actual process could still be runnin gin the background. If you can't find the buggy program directly by looking at the memory usage of your processes then you simply have to start systematically monitoring the programs you run to find the problem. Don't run all the apps, just start one app you normally use, let it run for a while, check the RAM usage, close the app and check RAM usage again. And repeat with everything you are commonly using. (of course if you have anything you have compiled from source, installed from a PPA repository or some other outside source that would be the first thing to check).

---

### Post by danastasio on 2010-01-05
> Remember, not only applications use memory and have bugs. Every single piece of software you run is the same, even if it's just some small background service, GTK theme engine or panel applet.

This is what i cannot figure out though. Even if I close all my apps, kill any processess that is associated with them and kill gdm, free -m still reports over 700 MB of program usage. That seems like an incredible ammount to run -just- a base system.

i'll trRemember, not only applications use memory and have bugs. Every single piece of software you run is the same, even if it's just some small background service, GTK theme engine or panel applet.y your second suggestion though.

---

### Post by smif1984 on 2010-01-18
Having the same annoying problem.. BTW do you have virtualbox modules installed?? I'm trying to debug this problem..

---

### Post by Ghost Hacks on 2010-01-18
I don't know a lot about Linux, but for example it's probably image caches and other files stored in ram, in case you need to access the file or data again, it will be pre-loaded to open faster, I don't see why your complaining as soon as you go to use the ram and it's needed the stuff not used will be deleted and then used for something else, btw don't use Windows Vista or 7, average ram use after boot is 1gb and after several hours around 1.5gbs, like I said 700mb is nothing, when most people have 2gbs of ram or more.

---

### Post by rnerwein on 2010-01-18
> **danastasio said:**
> Right, I understand caching and buffers and whatnot, but what i dont understand is that when my computer starts, it uses ~340 MB of RAM system wise, free -m AND system monitor applet both show this (11% in use by PROGRAMS), this is when nothing but gnome-do is running, so why, after i close every program after hours of use, free -m and sys applet both report ~1 GB in use by PROGRAMS and a whole lot more as cache. Is something being mistaken as a program thats actually cache? (i know that sounds impossible but -I- never know :P)

Thanks for the replies!

free -m

```
dave@dave-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3018       2367        651          0        173       1403
-/+ buffers/cache:        789       2228
Swap:         8911          0       8911

```NOTE: im totally ignoring the "free" field, just the -/+ buffers/cache field is what im paying attention to.

So i guess my question really is: why are "programs" (not cache) using so much RAM when nothing is running.

hi
i think that jocko and bodhi.zazan have explain it very good and here i'll will give a hint that will give a little bit more satisfaction.
have a look at /proc/iomem (you must be a little bit confirm with hex calculation) there you will see acatly where your ram is going (and needed).
if on the other side - if it makes you happy (i see you have 3 gb ram)
open a terminal and cd /tmp --> dd if=/dev/zero of=bla bs=4k count=500000
--> free -m --> don't panic ! --> rm bla --> free -m --> bee happy now :D and i think now you know what's going on
ciao

---

### Post by danastasio on 2010-01-18
> Having the same annoying problem.. BTW do you have virtualbox modules installed?? I'm trying to debug this problem..


No I don't have virtualbox modules installed, however I seem to have found a solution, While this had plauged most Ubuntu versions I had used, the problem was happening in Lucid Alpha 1 and 2. Though I found if I stopped using the Nvidia driver from 7machines ppa, and use the driver from the Nvidia website, my RAM usage went back to what I was expecting / had seen in other distro's.

To everyone who keeps insisting on suggesting on telling me that its the cache... thank you very much for the reply's, but... please stop. I have already explained that I -know- what cache is and how its used, I have also explained that I know how to tell how much is being used for cache at any given time. I was NOT talking about the cache, but the ammount of RAM being used by PROGRAMS.

> I don't know a lot about Linux, but for example it's probably image caches and other files stored in ram, in case you need to access the file or data again

I do know quite a bit about linux and i know what caching is and i keep saying that it is -NOT- see that? NOT cache, but RAM in use by programs, to me this is a waste of RAM, and should not be happening. I've used -many- other distro's and Ubuntu is the only one to display this behavior. I dont use windows anything on my computer, but that has nothing to do with this topic.

---

