---
title: "Memory leak after closing programs HELP!"
date: 2010-11-28
forum: General Help
---

### Post by nolag on 2010-11-28
When I run free -m after boot I get 609MB used.  When I open and close Firefox (I restored all the config stuff I changed and rebooted), or eclipse, the free -m says more memory is being used!  I don't know why and I see that after closing a few browsers and eclipes I have 906 in use (I am running one ff to post this).

Please help.

---

### Post by mikewhatever on 2010-11-28
Can you post the output of free -m.

---

### Post by nolag on 2010-11-28
now (one ff running, that's all):
             total       used       free     shared    buffers     cached
Mem:          3950        959       2991          0         47        372
-/+ buffers/cache:        539       3411
Swap:            0          0          0

boot:

             total       used       free     shared    buffers     cached
Mem:          3950        609       3341          0         42        158
-/+ buffers/cache:        407       3543
Swap:            0          0          0

in between (either there are no ff or one ff running):

             total       used       free     shared    buffers     cached
Mem:          3950        834       3116          0         44        253
-/+ buffers/cache:        535       3414
Swap:            0          0          0

I did many in between.  After closing things the memory does not seem to free.  I also opened and closed ecplipse (to see if it was just ff), and I did not get all the memory back (in fact that seemed to be the biggest leak).

---

### Post by mikewhatever on 2010-11-28
It's somewhat confising, but you should look at the first number in the second line because that's the memory used for programs. That number should indeed change when you open/close programs.
The second number in the first line shows the total used memory, programs + cache. 
All in all, it doesn't look like a memory leak.

---

### Post by nolag on 2010-11-29
> **mikewhatever said:**
> It's somewhat confising, but you should look at the first number in the second line because that's the memory used for programs. That number should indeed change when you open/close programs.
The second number in the first line shows the total used memory, programs + cache. 
All in all, it doesn't look like a memory leak.
 
Wait, the 1st one is total avalible for programs + cache (so I have 4GB RAM, but ubuntu uses some so it has 3950MB left). 
 
2nd number is the amount that I have used. At boot it was 604MB, afte a few firefoxes open then closed, I was using 834MB (should be 604MB since nothing was open), after closing eclipse I had 959MB used (one firefox was running, but that would not take over 100MB of RAM and when I closed it it did not go back to 604MB or even 834MB).
 
In this case the RAM useage went from 604MB to 834MB with nothing open, to 959MB with only one firefox open... This is a HUGE usage for almost nothing (and the 230MB with nothing open is confusing for sure)...

---

### Post by mikewhatever on 2010-11-29
You lost me there. Let's take apart the first free -m output you posted. It looks much better when properly formatted.

```
     total used free shared buffers cached
Mem: 3950  609  3341     0      42    158
-/+ buffers/cache: 407 3543
Swap: 0 0 0

```total used free shared buffers cached

3950 -total RAM available
609  -total RAM used for running processes + cache + buffers
3341 -free RAM

609MB is only about 15% of the total RAM, nothing to worry about.

---

### Post by nolag on 2010-11-29
> **mikewhatever said:**
> You lost me there. Let's take apart the first free -m output you posted. It looks much better when properly formatted.
 
```
     total used free shared buffers cached
Mem: 3950  609  3341     0      42    158
-/+ buffers/cache: 407 3543
Swap: 0 0 0

```total used free shared buffers cached
 
3950 -total RAM available
609 -total RAM used for running processes + cache + buffers
3341 -free RAM
 
609MB is only about 15% of the total RAM, nothing to worry about.
 
 
That was what it started off as.  Then it went to
 
         total used free shared buffers cached
Mem: 3950 834 3116 0 44 253
-/+ buffers/cache: 535 3414
Swap: 0 0 0

 
225MB more RAM in use with nothing open.  After that I opened eclipse, and closed it.  I then opened ff

          total used free shared buffers cached
Mem: 3950 959 2991 0 47 372
-/+ buffers/cache: 539 3411
Swap: 0 0 0

 
959MB of RAM for only one ff is a LOT.  I closed it and still did not even go back to the 838MB!  When I close stuff it won't kill off the memory it was taking!  Before all this I noticed almost all 4GB in use after closing a reasource Ubuntu Customization Kit.  I assumed it closed incorrectly and rebooted.  That was when I started to monitor it.  I had rebooted twice and the same type of thing kept happening!

---

### Post by mc4man on 2010-11-29
You're looking at the wrong line - see blue
```
doug@doug-XPS-M1330:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3021        559       2462          0         55        235
-/+ buffers/cache:       [COLOR="Blue"] 269       2752[/COLOR]
Swap:          475          0        475

```
The memory is cached which is what you want (the more the better
If you've ever noticed when you start ff from a fresh boot it takes longer than restarting ff in a session.

---

### Post by Slim Odds on 2010-11-29
This issue is one of the most repeated "problems" that newbies report. I don't have the list/post handy, but look around in thes forums because this has been explained many times. Yes, it's called caching and that memory is available when your programs need it.

MS Windows does exactly the same thing.

Note that there was a big stink when Windows 7 came out because some people misinterpreted its "free" memory reporting in **exactly** the same way.

---

### Post by nolag on 2010-11-29
> **mc4man said:**
> You're looking at the wrong line - see blue
```
doug@doug-XPS-M1330:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3021        559       2462          0         55        235
-/+ buffers/cache:       [COLOR=blue]269       2752[/COLOR]
Swap:          475          0        475

```
The memory is cached which is what you want (the more the better
If you've ever noticed when you start ff from a fresh boot it takes longer than restarting ff in a session.
 
Ok, I got you.  If I was to use some resource hungry app (say burn a DVD) that needed the RAM, then the cache would be cleared and reused right (as opposed to swapped)?  At that point ff would take as much time as the first time it loaded.  I did not relize that the cache was kept for ff (and I guess other apps) when there are none running, I thought it was only for if you want 2 open the second will not take as long.

---

### Post by mikewhatever on 2010-11-29
> **nolag said:**
> ...
 
959MB of RAM for only one ff is a LOT.  I closed it and still did not even go back to the 838MB!  When I close stuff it won't kill off the memory it was taking!  Before all this I noticed almost all 4GB in use after closing a reasource Ubuntu Customization Kit.  I assumed it closed incorrectly and rebooted.  That was when I started to monitor it.  I had rebooted twice and the same type of thing kept happening!

That's not for Firefox only, but the total memory usage - all running processes + all buffers + all the cache.
There are actually quite a lot of stuff running in the background without you opening anything. Run **ps -A** to see the list of all running processes.

---

### Post by Slim Odds on 2010-11-29
It's a disk cache. _Anything _read from disk remains in the cache until that memory is needed by something else (program or data).

That way the disk does not have to always be reread for every thing, it just gets retrieved from memory instead of disk (saves time and energy).

---

