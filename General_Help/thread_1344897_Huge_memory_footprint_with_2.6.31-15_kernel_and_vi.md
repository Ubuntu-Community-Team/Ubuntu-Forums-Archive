---
title: "Huge memory footprint with 2.6.31-15 kernel and virtual box kernel module enabled."
date: 2009-12-03
forum: General Help
---

### Post by cormano on 2009-12-03
Thats it, for some reason, only happens with the latest kernel, and not with the .14 version that originally started in karmic.
Usually, my system has about 140 mb used just after boot, but when i use the latest kernel and the vbox kernel module is active, memory use skyrockets to 400-500 mb just after boot. 
Ive checked with gnome-system-monitor and i cant trace what process is taking all that memory, aparently none, i mean all the processes show normal numbers...
My system is a core2duo on a p43 chipset asus p5qlpro, with 2gb of ram installed, and an nvidia 7900gt gfx with the binary nvidia driver. 
Has anyone else experienced this issue too? Any thoughts?

---

### Post by verduler on 2009-12-05
I have the same problem with the 2.6.31-15 kernel.

---

### Post by cormano on 2009-12-13
It seems to be happening with .16 too. I wonder if we are alone in this.
For the time being ill stick to .14

---

### Post by salemboot on 2009-12-29
anyone reported the bug on launchpad?

---

### Post by ElTimo on 2010-01-09
You're not alone in this. I'm having the same problem as well. Asking on the irc room has only gotten me answers of the nature "Dude, you have 2 GB of ram, what are you worrying about?"

I've had this problem even after recompiling my kernel, stripping out all of the debug symbols and optimizing it for my particular processor (which I recommend doing regardless, if you have the time).

---

### Post by trifthen on 2010-01-12
Ugh! I just noticed this myself. But I'm not sure it's related to VirtualBox. I've removed VirtualBox entirely, no trace on my system, modprobe says it's not installed. And yet?

Even with "sudo system gdm stop" and basically every user process shut down, I have over 600MB used after subtracting buffers and caches. WTF? I can't find any explanation for that at all, and nobody else seems to have said anything. But having my "right after reboot" memory increase from about 200MB to 850MB was pretty hard to ignore.

Is it the kernel or what? What's going on?

---

### Post by ElTimo on 2010-01-12
I'm thinking it is. I don't have VB installed either, and my footprint immediately after reboot is much much higher than with Jaunty or any of the previous releases. I just can't for the life of me figure out what part of the kernel is causing it. I'll keep playing with the kernel config and see if anything helps.

---

### Post by warfacegod on 2010-01-12
Why don't you guys try the -17 header. I'm using it and getting no loss. It's possible that the video driver could be causing a leak.

---

### Post by ElTimo on 2010-01-12
I am using the -17 kernel. That's where the problem is. The -14 kernel was less bad, but still pretty whorish in terms of memory usage. What video card does everyone use? I'm using an nVidia Quadro 110m, using the 185.x driver.

---

### Post by warfacegod on 2010-01-12
I'm using nVidea 5200Go 64 MB with the 173 driver. I've seen this once or twice with the newest ATi drivers.

---

### Post by ElTimo on 2010-01-12
The problem definitely seems to be kernel-related. I just tried out kernel 2.6.33rc3 from the kernel mainline ppa, and my memory usage dropped to ~400 MB, which, while still more than I'd like to be using, is a lot better. I'm curious as to whether any other distributions suffer from this problem. I'll try out Mandriva and Suse and see how they run.
If all else fails, I'm going back to Jaunty. At least it wasn't a memory slut like Karmic is.

---

### Post by Leppie on 2010-01-12
it seems like you all have nvidia graphics, you might want to try another version of drivers as warfacegod suggested.

---

### Post by trifthen on 2010-01-13
Hey, before getting to far into this, check to make sure it isn't [Bug 501715](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715) first. I too [noticed memory issues](http://ubuntuforums.org/showthread.php?t=1379275) that weren't reported by top or ps. Turns out ureadahead was borked somehow and kept holding 500+MB of my memory.

Rebooting twice in a row without logging in fixed it for me, but who knows if it'll return if I reboot again. You might want to check what removing ureadahead does for you.

---

### Post by lavinog on 2010-01-13
I also have more information here: [http://ubuntuforums.org/showthread.php?t=1363165](http://ubuntuforums.org/showthread.php?t=1363165)
It was originally posted in the server section because it was noticed first on my server.

---

### Post by ElTimo on 2010-01-13
Removing ureadahead (and thus, as a dependency, sreadahead) alleviated the problem a bit, but still not as much as I'd like. Back on Jaunty, my after boot memory usage was 200-ish MB. I'm down to about 490 now, but I still want less!! (I'm picky, I know).

For those of you who wonder why I'm so picky about memory usage, I used to use a Gateway S400 with 256 MB of RAM...it ran XP Home. I generally had less than 20 MB of free memory at any given time.

So there's my reason for wanting to cut down the kernel.

---

### Post by lavinog on 2010-01-13
How are you determining your boot memory?

can you post
```

free -m

```
For example:
```

             total       used       free     shared    buffers     cached
Mem:           997        299        698          0         33        113
-/+ buffers/cache:        152        845
Swap:          321          0        321

```
My memory usage is 152 megs.  Even though it says 299 used, the cache and buffers are for speeding up the system and are not actually preventing me from using more memory.
This is a fairly fresh lucid install.
There are some things that could be disabled to reduce this further, but I am using it for testing, and don't want to deviate too much from a standard install.

---

### Post by ElTimo on 2010-01-13
I'm using `free -m`, and the memory usage WITHOUT the buffers is 670 MB. INCLUDING the buffers it's ~2 GB.

---

### Post by lavinog on 2010-01-13
> **ElTimo said:**
> I'm using `free -m`, and the memory usage WITHOUT the buffers is 670 MB. INCLUDING the buffers it's ~2 GB.

That can't be right after a boot though. Is there anything running when you checked that?

---

### Post by ElTimo on 2010-01-13
It's as close to "right after boot" as I can get it. And that's with nothing running. See why we're confused? :P

---

### Post by automaton26 on 2010-01-17
After booting my Kubuntu x64 9.10 (with -17 kernel), I get:

```
             total       used       free     shared    buffers     cached
Mem:          3956       1045       2910          0         37        647
-/+ buffers/cache:        360       3596
Swap:         4110          0       4110
```

That's as bad as Windows Vista ;)

It was a few hundred when I used 9.04. And I'm using ATI Catalyst 9.10, so it's not necessarily nVidia related.

The [ other thread]("http://ubuntuforums.org/showthread.php?t=1363165") mentioned above sounds the same, but there's no sign of a cure.

Grrrr...the next LTS release has really got to improve things.

---

### Post by automaton26 on 2010-01-17
UPDATE: I've removed "preload", and after a few reboots I get a more satisfactory:
```

             total       used       free     shared    buffers     cached
Mem:          3956        673       3282          0        111        214
-/+ buffers/cache:        347       3609
Swap:         4110          0       4110

```

Perhaps "preload" should be uninstalled & reinstalled every time the kernel gets upgraded (just like I have to do for my ATI Catalyst driver package).

Anyway, I'll leave "preload" uninstalled for a while ;)

---

### Post by lavinog on 2010-01-18
> **automaton26 said:**
> UPDATE: I've removed "preload", and after a few reboots I get a more satisfactory:

You went from 360M to 347M.  Removing preload just reduced your file cache.
Vista uses a lot more than 360M.  It barely functions with only 512M in vista basic.

---

### Post by trifthen on 2010-01-18
> **lavinog said:**
> Vista uses a lot more than 360M.

Awwww, give the guy a break. :)

My system, even with PostgreSQL, BIND, and a couple other random things running at startup, uses about 90MB according to free. This is of course with GDM still running. Buffers and Cache bring it up to 365. So, what is eating this poor guy's other 260MB?

Sure, he has 4GB, so 260MB is pretty much child's play, but what if he were using a netbook with 1GB of RAM? Would it matter then? I know that's what led me to track down the ureadahead problem, which seems to *not* be his issue, oddly enough.

---

### Post by lavinog on 2010-01-18
try this command:
```

ps aux|sort -r -k 1.22|head

```

---

### Post by trifthen on 2010-01-18
This will be a little more accurate:

> ps axo rss,command:50,pid | sort -nr | head

Not sure why, but that other command put opera fifth down the list even though it was clearly the winner in terms of memory usage. :p

---

### Post by lavinog on 2010-01-18
> **trifthen said:**
> This will be a little more accurate:



Not sure why, but that other command put opera fifth down the list even though it was clearly the winner in terms of memory usage. :p

I forgot the -n switch.

---

### Post by automaton26 on 2010-01-19
> **lavinog said:**
> Vista uses a lot more than 360M.

Lol. you're right - I meant XP, and was just looking at "used Mem" - doh :\

I suppose my memory usage will be quite different to the OP, as I have KDE & amd64.

Anyway, removing preload made my system snappier again on reboot, which is all I was after.

Sorry for going off-topic there :)

---

### Post by lavinog on 2010-01-19
> **automaton26 said:**
> Lol. you're right - I meant XP, and was just looking at "used Mem" - doh :\

I suppose my memory usage will be quite different to the OP, as I have KDE & amd64.

Anyway, removing preload made my system snappier again on reboot, which is all I was after.

Sorry for going off-topic there :)

Did you remove preload or ureadahead?
Doesn't ureadahead do the same thing as preload?
Or is preload used to speedup launching programs after boot?

---

### Post by colinjones on 2010-01-21
also seeing the same thing, immediately after boot, 400+ MB, using -17 kernel, 64bit, 9.10. (and enormous amounts of vmem, but that's a different story!)

after a while of running, but closing all my apps, I have about 400MB FREE from a total 2GB physical, but the mem consumed by processes doesn't add up to anywhere near this amount.

It is obviously also forcing swap to be used, as normally this is practically untouched in my usage patterns, but I'm seeing it shoot up to 6-700MB .... something is sucking up physical RAM but it appears to be invisible...

---

### Post by lavinog on 2010-01-22
deleted

---

### Post by salemboot on 2010-01-28
I don't think 64bit gets tested like the 32bit distribution does.


Rolling back to the 2.6.31-14 kernel works fine for me.  

I looked in the -17 source. Only things that stuck out to me were the dynamic ticks being enabled, 64 cores as the limit (lower it to 2), and 100 MHZ clock (use 1000mhz).  

That should get the performance back up.  Generally speaking you don't go dropping the clock for desktop units.

---

### Post by Chromagnum on 2010-02-07
First time around here--so, hi. 

I'm really new to Linux and Ubuntu environment, and been using Karmic Koala for about 2 months now. I notice the same problem with the huge memory thing also happens to my computer. My system are P4 3ghz dual core, 1 GB RAM, and Nvidia 5500 fx.

I've been roaming around for the same kind of topic about huge memory consumption and leaky ones--and still I don't understand. It seems to me (for the reasons I don't understand or perhaps it is what it is) if I didn't reboot my system for a long period of time (let's say about 3 or 4 days) and the memory from around 300mb goes up to about 600-700mb, idle condition; particularly nautilus.

Instead of reboot, I just performed "killall nautilus" and called it back again using alt+F2. That seem to solved the problem. From around 14-15mb to hugely 300++mb and came back to 14-15mb again.

On the other hand, if I used browser with around 8 or 10 tabs (Chromium, btw) also with Pidgin and Songbird running, I had to gave up Songbird or cut it back browser to around 4 tabs, because if I didn't do that--holy crap!--it would be hard to move around from tab to tab; the delay is killing me.

Once again, I'm really new to Ubuntu so please bear with me. I mean... spare my life. Lol.

PS: English is not my native language, so... yeah. Spare me with this one too.

Chromagnum out. Cheers guys.

---

### Post by lavinog on 2010-02-08
@Chromagnum:
It is important to understand how memory works in linux.  How are you determining your memory usage?
if you type **free -m** in a terminal, you will get some information about memory usage.
```

free -m
             total       used       free     shared    buffers     cached
Mem:          1380       1166        214          0        153        690
-/+ buffers/cache:        322       1057
Swap:          533          0        533

```
If you notice: the used memory here says 1166 mb, and the free memory is 214mb.  But 690mb is cached memory which is technically free memory used to speedup disk access (kind of like windows readyboost but much better.)
Generally in the linux community you will hear "Free memory is wasted memory" for the reason that free memory does not improve system performance.

This thread though, is referring to unusual high memory usage right after boot that cannot be accounted for (The kernel is hogging the memory)  This is determined by looking at the -/+ buffers/cache: line and comparing it to past boots.

---

### Post by colinjones on 2010-02-08
To add to lavinog's comments, and be more explicit - the value you should be looking at is the 322MB is that example. This is the actual amount of memory being consumed.

(lavinog - much is made of what Linux does with caches and buffers to speed things up, and regularly people comment on the difference between it and Windows not doing this. I would like to point out that this is not accurate! Windows has always done basically exactly the same thing! If you look in Task Manager, you will see System Cache consuming large amounts of RAM too... that's what it is. Its caching files as it accesses them, and releasing that memory as processes need it. The only real difference is Windows doesn't have confusing tools like "free" that muddy the water :) but yes, I still hate Windows!)

---

### Post by lavinog on 2010-02-08
> **colinjones said:**
> 
(lavinog - much is made of what Linux does with caches and buffers to speed things up, and regularly people comment on the difference between it and Windows not doing this. I would like to point out that this is not accurate! Windows has always done basically exactly the same thing! If you look in Task Manager, you will see System Cache consuming large amounts of RAM too... that's what it is. Its caching files as it accesses them, and releasing that memory as processes need it. The only real difference is Windows doesn't have confusing tools like "free" that muddy the water :) but yes, I still hate Windows!)

Yes windows does cache files too, but not as aggressively as linux:
[http://www.techspot.com/tweaks/memory-winxp/](http://www.techspot.com/tweaks/memory-winxp/)
> 
Memory usage. This setting controls the size of the file system cache. When set to Programs (Default) a standard sized file system cache is allocated (Less than 10MB RAM); this is recommended as it provides best Application performance. When set to System cache this enables the use of a large file system cache (Up to RAM minus 4MB!); this option is only suitable when Windows XP is acting as a Server not as a gaming system or for other Application/Workstation use as it will be detrimental to performance as Microsoft notes:

Granted this is windows xp and not a newer version.

---

### Post by colinjones on 2010-02-08
Understood, and agreed! The comment wasn't so much directed at you - do a search for any thread talking about memory usage on the forums, and almost invariably, someone will make the comment that Linux caches files, whereas Windows does not *at all*.

Its misinformed, and I thought the point should be made :)

In any case, the extract you quoted is not accurate! I'm using an XP machine now, set to "Programs", and it is currently using 670MB for the System Cache. This is perfectly normal, if you do some Google searches on the subject you will find plenty of people reporting similar numbers. The System Cache maps I/O pages from disk access for reading and writing, not just entire files. The File Cache is a subset of the System Cache, I believe that is what is limited in size, whereas the System Cache overall expands to use all unallocated memory if necessary (same as Linux, and most other OS's for that matter)... presumably because whilst caching entire files is handy, its more flexible and efficient to cache individual pages of a file, so you want the System Cache to concentrate on that.

---

### Post by Chromagnum on 2010-02-09
Thank you lavinog and calinjones for the explanation. I think I'm beginning to understand a little bit. 

I sincerely apologize to the thread owner for barging in onto the wrong discussion.

I still have some questions but perhaps I should find similar thread or start a new topic. Yeah, that seems appropriate.

Regards,
Chromagnum.

---

