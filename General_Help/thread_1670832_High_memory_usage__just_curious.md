---
title: "High memory usage | just curious"
date: 2011-01-19
forum: General Help
---

### Post by kimyoungil on 2011-01-19
Hi,
I noticed that my RAM usage is quite high: 1.7gb ram used, 1.1gb swap used.
But I can't find out where the ram goes.
If I count together all used ram (see attachment), I get around 1.2gb, not even half of what's used.

```

$free -m
             total       used       free     shared    buffers     cached
Mem:          2008       1960         48          0         27        223
-/+ buffers/cache:       1710        298
Swap:         6000       1126       4874

```

At this moment my computer is starting to become somewhat slow because of the swap usage. 

Maybe I should mention that I often use "hibernate" (around 15 times since last reboot) Does this slowly consume my ram? After a restart my ram usage often is lower.



It's not a really big problem to me, I'm more interested to find out where my ram has gone.

---

### Post by 3Miro on 2011-01-19
Linux is optimized to take maximum advantage of all the RAM that you have. If you are using 1GB of 2GB, then you are wasting RAM and this is bad. Linux caches files from your harddriver, whether those are programs, shared libraries, media or whatever else. As a result of that, unless you are looking immediately after boot (and things will be a bit fuzzy there too), there is absolutely no way to accurately determine how much memory you are "using".

The high swap usage is probably due to hibernation.

In general, the system will use less memory and be overall smoother, if you don't mix applications from different environments. For example, it is highly recommended to use Dolphin instead of Nautilus (unde KDE).

One Important Note: when you post screenshots, you may want to edit them to hide any private information. I can see the files that you have opened with nautilus among other things. You should probably remove the picture that you currently have.

---

### Post by kimyoungil on 2011-01-19
I'm using gnome, but ksysguard has some more options. Normally I don't mix things.

But looking at the programs I use, I shouldn't need any swap, and there should be plenty of RAM free. But my swap-partition is used quite a lot (it's a noisy disk, so I can hear it when it's used)
If programs are using 1.2gb, it's a bit strange that there 1.1gb swap in use. 

I've read that "free -m" does give a good estimate, as long as you look at -/+buffer: used; 1710 mb in my case. So it seems to be almost full.

about the picture: there's nothing interesting to see. (I did look at it)



Well, maybe there's no way of knowing what memory is used where. But that seems a bit strange to me.

---

### Post by oldos2er on 2011-01-19
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by 3Miro on 2011-01-19
You want to use all of the 2GB of system RAM at all times and as little swap as possible.

You are not using 1.2GB of Swap, part of it is cached. If you need only a little bit of swap now and then, the swap will slowly grow to max level just like the regular RAM. Old information is not removed from the swap, why remove it when you can keep it there.

My guess is that this is left over from the hibernation process (which uses swap), however, if you are hearing the HDD working, you can try changing the "swappiness" of the kernel (look for swappiness).

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

It is also possible that you used a lot of swap in the past, and now it is just staying there. If I mess up a MATLAB program and use too much RAM to go on the swap, the swap will keep on saying X amount used until I reboot (which may be for weeks).

---

### Post by 3Miro on 2011-01-19
Double-post

---

### Post by 3Miro on 2011-01-19
Tripple-post

---

### Post by lithopsian on 2011-01-19
None of these cookie-cutter replies answer the basic query.  The original question was why, *excluding cache and buffers*, free reports 1.7GB of memory used (and so does the Memory Monitor summary for that matter) but that 1.7GB is not readily visible as belonging to processes.  I don't know the exact reason for this although I think there is a bit more than 1.2GB showing in those processes and also one or two things that aren't being shown.  I don't know the exact type of memory being reported by that utility but it can be very confusing all the different types of memory that get reported.  Do "ps aux" for example and you'll see three different kinds reported for each process.

So ignore anyone talking about caching anything.  It may be true but it is irrelevant.  Equally, since you claim you shouldn't need swap, read what they said because you do need swap.  I'm not convinced it is left over from hibernation but it has been used for something.  You have quite a lot of applications open and every single one of them will have a few (or many!) pages that get used perhaps at startup and then never again, or at least very rarely ever again, so they eventually get paged out.

> You want to use all of the 2GB of system RAM at all times and as little swap as possible.
Ignore rubbish statements about using as little swap as possible.  Use as much swap as necessary, but no more than necessary.  In an ideal world this is every page that you will not need to use again which can be quite considerable.  In practice Linux sometimes gets rid of pages that it does need to use again and if this happens too often then you will notice a sharp slowdown because disk is thousands of times slower than memory.  You'll either have to stop what is causing too much paging or adjust the kernel's enthusiasm for paging.  Lower swappiness will reduce your disk cache and somewhat slow down everything but will reduce the number of swapped application pages that need to be read from disk.  It is a balance, but the correct balance is most definitely not to aim for no swap.

> You are not using 1.2GB of Swap, part of it is cached.
I have no idea what that means.  Swap is not cached.  Swap is a completely different form of HDD access to reading a file and it does not go through a disk cache.  There is a very specific feature of recent Linux releases that will compress some of your swap pages and store them in main memory.  If you have this configured (compcache/ramzswap) then you could be using several hundred (compressed) MB of main memory for this, which will also be reported as about three times as much (uncompressed) swap pages.  Examine /proc/swaps to see if you have a /dev/ramzswapx device.

There also seems to be some statements that swap will never reduce.  It most definitely will reduce and you will often see the amount of swap go down, but with steady system use it tends to slowly rise to a level that you might find surprisingly high and stay at about that level.  If you use a memory hog application and then close it, you will likely see your swap drop slowly for a while afterwards.

---

### Post by 3Miro on 2011-01-19
> **lithopsian said:**
> None of these cookie-cutter replies answer the basic query.  The original question was why, *excluding cache and buffers*, free reports 1.7GB of memory used (and so does the Memory Monitor summary for that matter) but that 1.7GB is not readily visible as belonging to processes. I don't know the exact reason for this although I think there is a bit more than 1.2GB showing in those processes and also one or two things that aren't being shown.  I don't know the exact type of memory being reported by that utility but it can be very confusing all the different types of memory that get reported.  Do "ps aux" for example and you'll see three different kinds reported for each process.


How did we not answer? My statement that "you cannot know how much memory Linux is actually using" is correct. Pretty much every utility for Linux will report different amount of RAM, depending on how it is counted. Linux has many different types of RAM/swap and they get counted different in different circumstances. oldos2er gave a link to a simplified explanation and a detailed technical discussion is beyond the scope of the help forum. Ultimately there is no sign that the OP's system is not functioning properly.

> 
So ignore anyone talking about caching anything.  It may be true but it is irrelevant.  Equally, since you claim you shouldn't need swap, read what they said because you do need swap.  I'm not convinced it is left over from hibernation but it has been used for something.  You have quite a lot of applications open and every single one of them will have a few (or many!) pages that get used perhaps at startup and then never again, or at least very rarely ever again, so they eventually get paged out.


Note that Linux caches not only HDD data (such as music files), but also libraries associated with programs (like media codecs). There are multiple types of RAM cache that can be displayed different by different utilities.

As for swap, my desktop will not use swap unless I use a bad program that takes up all the memory (or run out of RAM for some other reason). My laptop will always use swap, especially when running on battery. If there is enough RAM for all the programs, swap should be used only for powersaving purposes. This can be adjusted as by the HowTo that I linked in an earlier post.

> 
Ignore rubbish statements about using as little swap as possible.  


Please, there is no need for this...

> 
Use as much swap as necessary, but no more than necessary. In an ideal world this is every page that you will not need to use again which can be quite considerable.  In practice Linux sometimes gets rid of pages that it does need to use again and if this happens too often then you will notice a sharp slowdown because disk is thousands of times slower than memory.  You'll either have to stop what is causing too much paging or adjust the kernel's enthusiasm for paging.  Lower swappiness will reduce your disk cache and somewhat slow down everything but will reduce the number of swapped application pages that need to be read from disk.  It is a balance, but the correct balance is most definitely not to aim for no swap.

I have no idea what that means.  Swap is not cached.  Swap is a completely different form of HDD access to reading a file and it does not go through a disk cache. 


Swap only provides two benefits, it allows you to run more programs than you can otherwise fit in RAM and it allows for some power savings. From software perspective, swap is different from regular file access, however, from hardware perspective, there is no difference. This means that swap is slow and HDD can be heard when the swap is working. 

There is no difference between reading a music file form the HDD or reading the codec that was previously swapped. If you swap pages of a program, then that program becomes slower. If you keep the program in memory and reduce HDD cache, then the program will wait longer, when it has to read form the HDD. It is true that if you have opened many applications AND you are not using a good number of them, then balanced swap usage will increase performance, however, it is much better to just close the unwanted apps and/or use apps that share the same libraries (like QT/KDE apps under KDE and GTK/Gnome apps under Gnome).

> 
There is a very specific feature of recent Linux releases that will compress some of your swap pages and store them in main memory.  If you have this configured (compcache/ramzswap) then you could be using several hundred (compressed) MB of main memory for this, which will also be reported as about three times as much (uncompressed) swap pages.  Examine /proc/swaps to see if you have a /dev/ramzswapx device.


I don't know if compcache will report as "swap", I guess this depends on the utility used, however, compcache will stay in RAM and not on the HDD. I guess this is one more type of memory that can be reported differently by different utilities.

> 
There also seems to be some statements that swap will never reduce.  It most definitely will reduce and you will often see the amount of swap go down, but with steady system use it tends to slowly rise to a level that you might find surprisingly high and stay at about that level.  If you use a memory hog application and then close it, you will likely see your swap drop slowly for a while afterwards.

If I have a bad program that takes up more RAM than I have, then I will see swap being used (as say 100MB of swap). However, if I close the bad program, swap will not "clear" for weeks. Whatever is written to the swap is there and there is no reason to remove it, not until all the swap has been taken up. Hence, if you have to use a little bit of swap, then you will see slow increase of swap usage up to a very high level (probably depending on the utility that you use).

---

### Post by kimyoungil on 2011-01-19
The swap usage can very well be from hibernating. As far as I know hibernation works more or less like putting everything to swap. Waking from hibernation only takes those things out of swap which are really needed. After hibernation there's always some swap used. (and that doesn't really bother me, after every program is used once, the computer is at normal speed)


@lithopsian: cat /proc/swaps gives no ramzswapx
However cat /proc/meminfo gives:
```
cat meminfo 
MemTotal:        2057128 kB
MemFree:           43524 kB
Buffers:           38312 kB
Cached:           391856 kB
SwapCached:       152964 kB
Active:          1183400 kB
Inactive:         575828 kB
Active(anon):     998832 kB
Inactive(anon):   353724 kB
Active(file):     184568 kB
Inactive(file):   222104 kB
Unevictable:        1860 kB
Mlocked:              32 kB
SwapTotal:       6144856 kB
SwapFree:        5553304 kB
Dirty:               160 kB
Writeback:             0 kB
AnonPages:       1270500 kB
Mapped:           125132 kB
Shmem:             21664 kB
Slab:             103376 kB
SReclaimable:      58608 kB
SUnreclaim:        44768 kB
KernelStack:        4424 kB
PageTables:        52672 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     7173420 kB
Committed_AS:    4349584 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      328760 kB
VmallocChunk:   34359399420 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:     1998784 kB
DirectMap2M:       98304 kB
```
```

 free -m
             total       used       free     shared    buffers     cached
Mem:          2008       1969         39          0         51        374
-/+ buffers/cache:       1543        465
Swap:         6000        577       5423
```
I did close some programs in the meantime. So things look less bad now.
But all programs together is still around 1.2gb, so this adds up to the "active" number im meminfo. There's still 300mb missing.
What do these (in)Active(Anon) things mean? I can't find what those entries mean. It must be somewhere in there, but I can't find a detailed explanation of what every column in meminfo means (well, nothing is up to date).

---

### Post by aaaantoine on 2011-01-19
> **3Miro said:**
> Swap only provides two benefits, it allows you to run more programs than you can otherwise fit in RAM and it allows for some power savings. From **hardware** perspective, swap is different from regular file access, however, from **software** perspective, there is no difference. This means that swap is slow and HDD can be heard when the swap is working. 

FTFY, I think, though technically the OS (software) is required to know the difference.  Applications don't have to know the difference, though.

According to kimyoungil, all his listed programs show RAM usage adding up to ~1.2GB, yet his system is using 1.7GB RAM *plus* 1.1GB Swap, a total of 2.8GB reserved for **running** programs.

I believe this warrants a second opinion, from the likes of, say, htop.

But in addition to that, try adding up the total of shared memory.

Either way, I smell a memory leak.

---

### Post by kimyoungil on 2011-01-19
double

---

### Post by kimyoungil on 2011-01-19
double

---

### Post by kimyoungil on 2011-01-19
double

---

### Post by kimyoungil on 2011-01-19
double

---

### Post by kimyoungil on 2011-01-19
Hmm, looks like I don't have to try to post again when the site returns an error :P



Adding all the swap together gives me 300mb, but when I look at an application using 30mb the shared size / number of apps using it is usually only 10% of it. So this 300mb total seems way too much. It's probably not more than 50.

---

### Post by kimyoungil on 2011-01-20
Does anyone know (or where to find) what the entries in /proc/meminfo really mean? All the information I can find is >5 years old and outdated. (there are a lot more entries now)
This has got to be documented somewhere. Or isn't it?

---

### Post by silvagroup on 2011-01-20
I too have seen something drastically change recently. My system was slower than STP in freezing temperatures.

I went from using 19-22% of memory with my system basically idling to 52-92% and 1.2mg of swap at times.
I have 3.5gb of ram on my system. 

Thinking it was bad memory ran test for a whole day, no errors, cheeked my wife's system same thing 92% memory in use, she only has 512mg. She used to run at 35%

I shut down compiz and everything that could be causing high usage and still have 
problem.

Free -m and top attached.

Also when I checked system monitor on both systems all processes show poll_schedule_timeout, do_wait, or do_signal_stop.
So it appears that something other than memory caching is going on, maybe? Not sure, but my system has most certainly bogged way down.

Todo we're not in Kansas any more.

---

### Post by kimyoungil on 2011-01-21
When I add together Shared Size + normal memory in ksysguard I get approximately the right total. But this seems strange to me, because adding all shared memory together should give a much too high estimate of the amount of memory in shared memory.


> I went from using 19-22% of memory with my system basically idling to 52-92% and 1.2mg of swap at times.
I have 3.5gb of ram on my system.
I'm not really sure if this is the same thing. Might be. Do you have lots of programs opened? You're using 1.8gb in the screenshot (excluding buffers/cache) How long since last reboot? I don't see any programs using much memory with top. Does it look the same in gnome-system-monitor? (maybe some inactive program is using most of your ram)

> Also when I checked system monitor on both systems all processes show poll_schedule_timeout, do_wait, or do_signal_stop.
As far as I know this is normal. This tells you what programs are waiting for to "do something" like waiting for mouseclicks etc.

---

### Post by silvagroup on 2011-01-22
> Do you have lots of programs opened?
NO, this was with system at idle, no programs other than system programs open and compiz off and nvidia drivers unloaded.
> How long since last reboot?
Night before about 14 hours.

This morning found my system frozen, had to hard start, attached screenshot.png is free -m after a fresh start and this is with compiz running. Screenshot-1.png is wirh Firefox in two separate windows one with 7 open tabs one window one tab open and of course all the addons.

I checked my laptop startup was the same at 19-22% didn't have much time so left it on over twelve ours later syetm frozen had to hard start.

Wifes system after over 12 hours shows 95% memory usage need to check fresh start stats on hers again.

> As far as I know this is normal. This tells you what programs are waiting for to "do something" like waiting for mouseclicks etc. 
This has NEVER been normal in the past, when I did system monitor and it show up on all three systems now. Need to check and see if there is some bug noted on this.

Will followup when I get back must go now, weekend my child has much going on so of course so does Dad. Lets how things stand when I get back in three hours.

---

### Post by matt_symes on 2011-01-22
Hi

What happens if you drop the caches ?

```
sync
echo 3 | sudo tee /proc/sys/vm/drop_caches
```

Could be a memory leak but it would be a big one.

Kind regards

---

### Post by silvagroup on 2011-01-26
Will try this, don't think it's memory leak but it is something on this system specifically.
Did recent updates on wifes system and it's now ok memory no issue with laptop either.
But over several days this system goes from 19-22% ram to 95%.
Maybe time for a fresh install, haven't had to do that since 7.10 probably time.
Will try your suggestion to see how things change.
Thanks.
PS
Just did it looking at free -m doesn't appear to have done anything will let it sit as is and check it again later on.

---

### Post by silvagroup on 2011-01-28
Well checking first thing this morning after dropping caches the system actually idling now for almost 24 hours ram up to 90% and to add to the problem recently have been having random system freezing not memory associated because this has happened while memory usage was still comparably low.

---

### Post by silvagroup on 2011-02-07
Since last post I have been able to (so far) get rid of the high memory usage.
It appears that I gnome keyring was doing something not sure what, but when I would enter my password it would ask for it several times assuming (we know what happens when we assume) that I mistyped it I would enter it again, always three times. 

In the process of diagnosing the mem problem I realised there was something a miss and so therefore carefully watched my typing and the key ring would ask for the password even though it was right
.
Now experimenting when I startup and keyring asks for the password three times I cancel it, and mem problem gone.

Any suggestions where to go from here? Be nice .....

---

### Post by silvagroup on 2011-02-13
Gnome key ring not the problem, issue still persistent, however running a livecd cd over many days did not replicate the increase in memory usage so it's certainly not a bad memory.
Very perplexing.

---

### Post by kimyoungil on 2011-02-19
Problem is back again. (I think) The system is still running fluently, but memory usage has increased again quite a lot.
uptime is 12 days, so that's after more than 12 times hibernating. (with kernel, not swsusp)
The problem might be the hibernation.


I must say that I did have the same problem with having to enter my password twice after logging in for unlocking the keyring. This might however very well be totally unrelated.
I do see polkitd using 100mb of RAM. Is this too much? I'm not sure, but I think polkit might have something to do with the keyring.


```

foo@bar:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2008       1721        287          0         41        240
-/+ buffers/cache:       1438        569
Swap:         6000       1331       4669
foo@bar:~$ top -n 1

top - 11:48:08 up 12 days, 13:36, 11 users,  load average: 1.56, 1.80, 1.97
Mem:   2057128k total,  1823472k used,   233656k free,    48200k buffers
Swap:  6144856k total,  1351940k used,  4792916k free,   284912k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                              
 2189 ik        20   0 1235m 401m  15m S 16.7 20.0 105:51.95 opera                                
 1349 root      20   0  356m 158m  11m S  6.8  7.9 456:25.54 Xorg                                 
 2237 ik        20   0 1215m 112m 9144 S  0.0  5.6  16:36.26 nautilus                             
 2206 root      20   0  158m 100m 1652 S  0.0  5.0   2:29.64 polkitd                              
23711 ik        20   0 1042m  70m  12m S 12.1  3.5 160:45.92 gmusicbrowser                        
 2114 ik        20   0  532m  44m 3924 S  0.0  2.2   3:54.99 gnome-settings-                      
12168 ik        20   0  517m  30m 6692 S  0.0  1.5   4:23.02 Mathematica                          
 2171 ik        20   0  465m  24m 6632 S  0.0  1.2   2:00.92 gnome-panel                          
 7009 ik        20   0  563m  23m 7276 S  3.1  1.2  57:04.84 transmission                         
 2211 ik        20   0  356m  19m  17m S  2.8  1.0 122:50.74 pulseaudio                           
 2126 ik        20   0  319m  19m 8344 S  4.3  1.0 214:54.98 compiz                               
 2406 ik        20   0  137m  12m 1940 S  0.3  0.6  18:58.00 ubuntuone-syncd                      
12635 ik        20   0  456m  12m 7372 S  0.3  0.6   0:21.77 gnome-terminal                       
 2298 ik        20   0  475m 9908 4904 S  0.0  0.5   3:39.14 wnck-applet                          
 2351 ik        20   0  489m 9740 4460 S  0.0  0.5   0:12.39 python                               
29714 ik        20   0  275m 9656 4424 S  0.0  0.5   1:39.44 notify-osd                           
 2215 ik        20   0  388m 9528 4552 S  0.0  0.5   1:52.74 easystroke                           
 2354 ik        20   0  417m 7916 4936 S  0.0  0.4   0:05.20 indicator-apple                      
 5467 ik        20   0  173m 6860 2116 S  0.0  0.3   0:04.93 zeitgeist-daemo                      
 2355 ik        20   0  422m 6820 3608 S  0.0  0.3   0:10.76 indicator-apple                      
 5486 ik        20   0  209m 6320 2100 S  0.0  0.3   1:57.26 zeitgeist-datah                      
 2288 ik        20   0  374m 5812 2680 S  0.0  0.3   1:18.88 gtk-window-deco                      
 1308 root      20   0 93672 5344 1516 S  0.0  0.3   0:05.44 NetworkManager                       
 2161 ik        20   0  285m 5092 3128 S  0.0  0.2   1:11.97 tilda                                
 2352 ik        20   0  301m 5028 3360 S  0.0  0.2   1:44.61 cpufreq-applet                       
30967 ik        20   0 23436 4856 1584 S  0.0  0.2   0:00.23 bash                                 
27173 ik        20   0 23436 4852 1584 S  0.0  0.2   0:00.34 bash                                 
 2231 ik        20   0  475m 4772 2596 S  0.0  0.2   0:05.01 nm-applet                            
 2356 ik        20   0  383m 4048 2440 S  0.0  0.2   0:10.09 clock-applet                         
 2283 ik        20   0  181m 4036 2548 S  0.0  0.2   1:10.53 gnome-screensav                      
12241 ik        20   0  328m 3924  136 S  0.3  0.2   2:22.63 MathKernel                           
 2353 ik        20   0  221m 3588 2492 S  4.6  0.2 224:59.66 multiload-apple                      
 2350 ik        20   0  399m 3280 1736 S  0.0  0.2   6:45.84 fish-applet-2                        
 2069 ik        20   0 57324 3272 1000 S  0.0  0.2   0:13.38 gconfd-2                             
 2300 ik        20   0  392m 2848 1832 S  0.0  0.1   0:01.44 trashapplet                          
 7715 ik        20   0  404m 2640 1300 S  0.0  0.1   0:12.16 kded4                                
13532 ik        20   0  816m 2500 1428 S  0.0  0.1   0:03.00 knotify4                             
15233 ik        20   0 42760 2460 1840 S  0.0  0.1   0:01.08 ssh                                  
13535 ik        20   0  375m 2416 1472 S  0.0  0.1   0:06.14 kwalletd                             
 2170 ik        20   0  372m 2408 1080 S  0.0  0.1   0:03.91 polkit-gnome-au                      
 2357 ik        20   0  200m 2348 1512 S  0.0  0.1   0:03.19 notification-ar                      
22470 ik        20   0  608m 2264  736 S  0.0  0.1  55:09.01 operapluginwrap                      
 1932 ik        20   0 27360 2180  416 S  0.0  0.1   4:18.19 dbus-daemon                          
13519 ik        20   0  399m 2108 1024 S  0.0  0.1   0:02.16 kglobalaccel                         
 2303 ik        20   0 98.2m 2088 1324 S  0.0  0.1   0:04.75 gvfs-gdu-volume                      
 2276 root      20   0 66388 2016 1264 S  0.0  0.1   0:33.06 udisks-daemon                        
 1205 messageb  20   0 25356 1924  480 S  0.0  0.1   0:37.20 dbus-daemon                          
30997 ik        20   0 11948 1848  912 S  0.0  0.1   0:00.04 man                                  
 2517 ik        20   0  233m 1816 1116 S  0.0  0.1   0:04.62 indicator-sound                      
 2272 ik        20   0  170m 1780  932 S  0.0  0.1   0:02.32 gdu-notificatio                      
 2202 ik        20   0  204m 1660  936 S  0.0  0.1   0:06.60 vino-server                          
 1741 ik        20   0  168m 1596  876 S  0.0  0.1   0:02.65 gnome-session                        
 8787 ik        20   0  255m 1560  788 S  0.0  0.1   0:04.32 gnome-power-man                      
28896 ik        20   0 23448 1556  832 S  0.0  0.1   0:00.65 bash                                 
 2524 ik        20   0  144m 1524 1080 S  0.0  0.1   0:01.27 indicator-sessi                      
 1434 mysql     20   0  249m 1496  120 S  0.0  0.1   3:48.35 mysqld                               
 2111 ik        20   0 98.1m 1492  428 S  0.0  0.1   0:01.02 gnome-keyring-d                      


```

edit: I did a swapoff -a and after that swapon. Also I killed a lot of programs. With a plain desktop, only transmission running and a few terminals I get:
This is better, but there's still 1.2Gb in use, which is a bit too much for a plain desktop.
When my downloads finnish I'll restart the system, so the memory usages can be compared.

```
op - 12:17:06 up 12 days, 14:05, 11 users,  load average: 0.89, 1.41, 1.66
Mem:   2057128k total,  1941860k used,   115268k free,    76864k buffers
Swap:  6144856k total,        0k used,  6144856k free,   509208k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                              
 1349 root      20   0  354m 235m  11m R  5.1 11.7 459:02.84 Xorg                                 
 2237 ik        20   0 1216m 179m  15m S  0.0  8.9  16:46.57 nautilus                             
 2206 root      20   0  159m 102m 1652 S  0.0  5.1   2:30.57 polkitd                              
 2114 ik        20   0  532m  72m 3940 S  0.0  3.6   3:57.01 gnome-settings-                      
11361 ik        20   0  247m  65m  11m D 11.9  3.3   0:01.19 opera                                
 2126 ik        20   0  319m  63m 8360 S  4.0  3.2 216:15.81 compiz                               
 2171 ik        20   0  465m  37m 6688 S  0.0  1.9   2:01.47 gnome-panel                          
 2406 ik        20   0  137m  29m 1940 S  0.2  1.4  19:03.46 ubuntuone-syncd                      
 7009 ik        20   0  563m  27m 7308 S  1.4  1.4  57:43.02 transmission                         
 2211 ik        20   0  292m  22m  19m S  0.0  1.1 123:27.45 pulseaudio                           
 2351 ik        20   0  489m  19m 4508 S  0.0  1.0   0:12.45 python                               
 1434 mysql     20   0  249m  18m  120 S  0.1  0.9   3:49.44 mysqld                               
 2163 ik        20   0  422m  18m  688 S  0.0  0.9   0:06.47 my-weather-indi                      
 2217 ik        20   0  211m  16m  560 S  0.0  0.8   0:01.19 ubuntu-sso-logi                      
 5486 ik        20   0  209m  15m 2104 S  0.0  0.8   1:58.97 zeitgeist-datah                      
13532 ik        20   0  816m  15m 1428 S  0.0  0.8   0:03.05 knotify4                             
12635 ik        20   0  456m  14m 7428 S  0.6  0.7   0:23.87 gnome-terminal                       
 5467 ik        20   0  173m  14m 2116 S  0.0  0.7   0:04.99 zeitgeist-daemo                      
 2215 ik        20   0  388m  13m 4584 S  0.6  0.7   1:53.96 easystroke                           
 2298 ik        20   0  475m  13m 5164 S  0.0  0.7   3:40.77 wnck-applet                          
29714 ik        20   0  275m  12m 4552 S  0.0  0.6   1:40.17 notify-osd                           
 2288 ik        20   0  375m  11m 4028 S  0.0  0.6   1:19.48 gtk-window-deco                      
 2355 ik        20   0  422m   9m 3768 S  0.0  0.5   0:10.82 indicator-apple                      
 2354 ik        20   0  417m 9444 4936 S  0.0  0.5   0:05.26 indicator-apple                      
 2231 ik        20   0  475m 8256 2596 S  0.0  0.4   0:05.04 nm-applet                            
  915 root      20   0 25664 8172  160 S  0.2  0.4   8:04.59 mount.ntfs                           
 1308 root      20   0 93672 7740 1516 S  0.0  0.4   0:05.46 NetworkManager                       
13519 ik        20   0  399m 7692 1024 S  0.0  0.4   0:02.20 kglobalaccel                         
 7715 ik        20   0  404m 7556 1300 S  0.0  0.4   0:12.26 kded4                                
 2111 ik        20   0 98.1m 7464  428 S  0.0  0.4   0:01.03 gnome-keyring-d                      
12467 ik        20   0 27032 7320  512 S  0.0  0.4   0:00.59 bash                                 
24588 ik        20   0 27088 6924    0 S  0.0  0.3   0:01.10 bash                                 
 2161 ik        20   0  285m 6916 3128 S  0.0  0.3   1:12.40 tilda                                
10913 ik        20   0 27044 6900   12 S  0.0  0.3   0:05.18 bash                                 
 5204 ik        20   0 27044 6888    8 S  0.0  0.3   0:02.16 bash                                 
27313 ik        20   0 27012 6848    0 S  0.0  0.3   0:00.72 bash                                 
 2300 ik        20   0  392m 6596 2504 S  0.0  0.3   0:01.45 trashapplet                          
13535 ik        20   0  375m 6564 1472 S  0.1  0.3   0:06.24 kwalletd                             
 2352 ik        20   0  301m 6524 3360 S  0.0  0.3   1:45.39 cpufreq-applet                       
 2356 ik        20   0  383m 6368 2440 S  0.0  0.3   0:10.14 clock-applet                         
 2350 ik        20   0  399m 6056 1736 S  0.3  0.3   6:47.98 fish-applet-2                        
 2283 ik        20   0  181m 5720 2548 S  0.0  0.3   1:10.93 gnome-screensav                      
 2353 ik        20   0  221m 5124 2492 S  4.5  0.2 226:14.75 multiload-apple                      
 2170 ik        20   0  372m 5076 1080 S  0.0  0.2   0:03.93 polkit-gnome-au                      
30967 ik        20   0 23436 4856 1584 S  0.0  0.2   0:00.23 bash                                 
27173 ik        20   0 23436 4852 1584 S  0.0  0.2   0:00.34 bash                                 
 2100 timidity  20   0  110m 4748    0 S  0.0  0.2   0:00.05 timidity                             
 2069 ik        20   0 57324 4644 1016 S  0.0  0.2   0:13.48 gconfd-2                             
  906 root      20   0 22264 4592   36 S  0.2  0.2  10:22.99 mount.ntfs                           
 2357 ik        20   0  200m 4220 1820 S  0.0  0.2   0:03.22 notification-ar                      
28140 ik        20   0  231m 4120    0 S  0.0  0.2   1:13.34 vim                                  
28896 ik        20   0 23448 4116  832 S  0.0  0.2   0:00.66 bash                                 
12650 ik        20   0 23448 4060  788 S  0.0  0.2   0:00.42 bash                                 
 8787 ik        20   0  255m 3852  788 S  0.0  0.2   0:04.36 gnome-power-man                      
 2202 ik        20   0  204m 3512  936 S  0.0  0.2   0:06.64 vino-server                          
 1932 ik        20   0 27360 3400  492 S  0.5  0.2   4:21.32 dbus-daemon                          
 2223 ik        20   0 23528 3356    0 S  0.0  0.2   0:00.65 bash                                 

```

---

### Post by silvagroup on 2011-02-19
Me too still having the same issues. Have tried several things with no change. Thought I had it solved once but it crept back. Have tried so many things actually forgot what I did to slow the thing down.

It's not a problem until it gets to 70 % or higher of memory and then the system just bogs down because of limited memory. to fix it I reboot and get my memory back for awhile.

I have pretty much given up on this one, I am just waiting for Natty then I am going to try a upgrade if that does nothing I will do a clean install and hopefully that fixes things. But I am thinking if I have to do a clean install I might as well just do a Debian install.

---

### Post by silvagroup on 2011-03-02
Latest updates appear to dramatically effect this issue. No longer Am I seeing 60+ seems  to now hoover around the 30s, which seems much more reasonable. Could be this is resolved can not say with certainty what it was that got fixed.

---

### Post by kimyoungil on 2011-03-04
Hmm, it seems it's not the memory usage which is causing a slow experience.

After running some time it seems that compiz slows down. When I login again it's fast.
What I did: Run my system for 5 days, close all programs, and then use the compiz-benchmark, I got around 80fps. 
Logout, and then in again: 360fp.
Both figures without doing anything.
You can figure what it would be like after 2 weeks.

That explains why multitasking got very slow after some time, it seems only the window manager has problems, not the system as a whole. 


(that and maybe some small memoryleaks in programs, but those leaks are comparatively small it seems)

---

### Post by silvagroup on 2011-03-04
thats intresting, on my system when I first started having the problem I shut off compiz and emarald and still had the problem and as far as I can recall my video driver has not been updated since the problem began so might be a different isssue with the systems.
Have you tried using metacity and gtk decorater and see if that gets rid of the problem. If it is compiz that shopuld stop it.
Latest system updates have so far dramatically improved my problem. The only problem I continue to have is my volume notification has a mind of its own and turns volume up and down at will.

---

