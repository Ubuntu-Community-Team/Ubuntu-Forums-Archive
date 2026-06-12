---
title: "Xubuntu memory using 1gig"
date: 2012-02-08
forum: General Help
---

### Post by sleepyhollows on 2012-02-08
Um I just installed Xubuntu 11.10 64, in the hope of lower memory usage than Unity.

It's using 1.2g! 

Ubuntu 11.04 is using 350megs!

Whats going on here! lol. I thought id finally found the right OS, I'd rather run a marathon than install another OS onto this dam server. lol

(btw, really struggling with unity's interface. Can't even find the About Ubuntu, know what I mean?)

Cheers
Mic

---

### Post by Toz on 2012-02-08
Hello and welcome to the forums.

First of all, nothing wrong with marathons :)

Secondly, type in the following command into a terminal window and post back the results:
```
free -m
```

The "used" value in the "-/+ buffers/cache:" row is the most accurate reflection of memory usage.

---

### Post by mörgæs on 2012-02-08
+1

More here:
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

Sorry for the ugly web design. The contents is fine, though.

---

### Post by sleepyhollows on 2012-02-09
I appreciate the computer science behind caching.

But..


I boot up 11.04 32bit, and mem use is 328 megs. Apparently 149 is cache.
On a 2gig machine.

I boot ub xubuntu, 11.10, 64bit, and its using 749, 336 cache
On a 1 gig machine.

Fresh boot, cache or no cache, at the end of the day, it's still using more memory.

Is it the 64bit-ed-ness?

Cheers

---

### Post by sleepyhollows on 2012-02-11
I've found the problem: 64bit

32bit Xubuntu uses 180 after fresh auto logon.
47 with lightdm stopped

64bit xubunut is using 350 fresh just after auto logon.
And 222 with light dm stopped.

If you do the math, the desktop interface is using 130megs.

So something in the underlying OS, on the 64bit version, is using a significant amount of memory as compared to the 32 bit version.

I wouldnt mind eliminating it, but then again, does any one really care about the 64 bit version ?? 

*All memory figures extracted using afore mentioned field from `free -m`
Cheers

---

### Post by sleepyhollows on 2012-02-11
Ok, so also XOrg is really high cpu usage compared to 32bit versions

And vino is awful slow.

I think ill just blow the 64bit version away and put on 32 bit :)

---

### Post by mörgæs on 2012-02-11
Good, then please mark the thread 'solved'.

---

### Post by 3Miro on 2012-02-11
On 64-bit machines the opcode part of a program is double in size. The data is the same, so the final result for a 64-bit program isn't necessarily 2 times larger, but it is always larger.

However, there is no reason for the CPU usage to be different like you describe. The Xorg thing might be a bug.

Either way, on a 2GB RAM machine 32-bit should work fine.

And yes, what mörgæs said, mark the thread as "solved".

---

### Post by sleepyhollows on 2012-02-12
I beleive the xorg thing and vino is due to my "server-grade" (read: crap) MGA graphic card.

Research on the net shows that 64bit is actually faster, especially since it enables providers to break i386 compatibility and enable all modern CPU features.

Plus, I have 12gig :)

Thanks all

---

