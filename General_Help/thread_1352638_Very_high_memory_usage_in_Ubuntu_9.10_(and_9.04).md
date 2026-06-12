---
title: "Very high memory usage in Ubuntu 9.10 (and 9.04)"
date: 2009-12-11
forum: General Help
---

### Post by FishFace on 2009-12-11
I've been getting awful memory performance for several months, through 9.04 and now in 9.10. It is now making the machine unusable, although the problem has been fairly severe for a while.

My machine is a laptop with 1Gb of memory on a near-clean installation, and I use it for browsing, IRC, email, IM and programming. The biggest hog is the browser (I've tried Chrome and Firefox 3.5) unsurprising since I have 10-20 tabs open usually. When I have the above tasks running concurrently (i.e. a browser, several clients open, and a bunch of gedit tabs open) doing just about anything such as changing tabs in Firefox causes a noticeable pause with some I/O. Launching a new application can result in minutes long pauses, and launching something fairly memory intensive will lock the machine up for more time than my patience can bear.

Under this kind of usage the Committed_AS statistic in /proc/meminfo is 1.5 Gb, which seems extremely high. Also, the amount of memory used on caches is extremely high - 600Mb or more. Not only that, but if I run out of main memory when there is still cached stuff in there, it doesn't immediately reap the cache, but locks up with disk I/O, I assume swapping. This occurs even if I set swappiness to 0, and echoing 3 to /proc/sys/vm/drop_caches makes little if any dent. (I did it just now and the cached memory dropped from 630Mb to 520Mb)

As an experiment, I tried disabling swap. Rather than ceasing thrashing and just OOM killing some process, though, when I ran out of main memory (with memory in the cache) the system locked up as usual with hard disk activity.

The problem appears to be twofold; firstly, there is an (in my opinion) inordinate amount of memory being consumed by what should be a fairly lean set of processes - the only hefty ones being Firefox and possibly X, and they should be better these days. Secondly, the system refuses to get rid of cached memory to make way for data that is really needed even if explicitly instructed to, causing premature OOM situations.

I have run a memtest successfully, and my HDD reports a pass on it's SMART readout.

Does anyone know if A) this situation is actually normal (i.e. I just have too high expectations) and B) if there is anything to be done. I would much prefer not to install more memory or a leaner DE since neither seems like it should be necessary (and the latter doesn't seem like it would have much effect.)

Thanks,
Fish.

---

### Post by PeEllAvaj on 2009-12-11
A few things you can try / look at are:
1. Try Xubuntu or Xfce (sudo apt-get install xubuntu-desktop). Xfce is a little lighter weight than Gnome.
2. Are you running the latest chromium-browser, or some version of Chrome?  With the latest chromium-browser, I can get 20-30 tabs only taking 200-300MB of RAM.
3. You said your browser is the biggest memory hog, what about 2nd or 3rd biggest hogs?

---

### Post by FishFace on 2009-12-12
I want to leave off using XFCE for as long as possible, since it seems to me that it shouldn't be necessary (I used to run worse, memory leaking versions of firefox on half this much RAM in GNOME previously!) and that it shouldn't have much effect on the core memory consumers since I will probably use the same apps - unless they all consume less RAM somehow when run under XFCE.

Yes, I'm using the linux dev build of chromium, although at the moment I have firefox running instead.

I did forget to mention that I usually have exaile running which also contributes its part to memory usage. Here's the first few lines of top:

```
 3894 fish      20   0  378m 143m  14m S    6 14.5  56:27.24 firefox            
 5426 fish      20   0  223m  42m  11m S    8  4.3   4:51.94 exaile             
 1121 root      20   0  222m  34m 9544 S    2  3.5  30:43.25 Xorg               
 4081 fish      20   0  213m  29m 8788 S    0  2.9   3:02.24 skype              
 5132 fish      30  10 76712  21m 6520 S    0  2.1   0:05.63 update-manager
```

As you can see, the virtual memory tally is huge on all these guys. I don't know where or whether that gets included in the consumed memory, since I don't believe I have enough memory + used swap to account for it all - there are 12 processes on the first page that have > 100M of virtual memory used, and four of those have > 200. I had 227M of Swap used at the time I copied that, and 973M of main memory (498 of which is caches)

---

### Post by salemboot on 2009-12-28
Ubuntu 9.10 64 bit here.

I'm turning around my comment.  It seems to be the kernel itself.

[http://ubuntuforums.org/showthread.php?t=1344897](http://ubuntuforums.org/showthread.php?t=1344897)

---

