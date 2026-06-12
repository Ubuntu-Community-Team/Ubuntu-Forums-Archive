---
title: "64b Karmic 3GiB quadcore: extremely slow swapping"
date: 2010-06-24
forum: General Help
---

### Post by original_MikZ on 2010-06-24
I've Googled a few times for solutions to this, but I haven't found any posts about quite the same situation as mine. Feel free to refer me to any I may have overlooked, and accept my apologies.

**My system:**

Ubuntu 9.10 (Karmic), Linux kernel 2.6.31-22-generic, GNOME 2.28.1.
Lenovo W700, 3.8GiB RAM, four Intel Q9000 2GHz processors

**The problem:**

Everything works great until the OS tries to swap memory. I can tell from looking at System Monitor: when memory usage hits 100%, everything grinds to a halt for a few seconds, apps start fading in and out, even System Monitor, and the amount of memory in swap changes. Apps fade back to grey again, it seems, when their memory is swapped back in. I need to run many memory-hungry apps, so this becomes very disruptive. I'm fortunate enough to work next to a window; it's a good thing it doesn't open, otherwise I might have thrown my computer out of it by now. :-x

**Details:**

I've tried changing swappiness from the default 60 to 10. I think this makes things stick less frequently but for longer, but I haven't recorded exact times so this could be my imagination. In any case, it's still quite suboptimal.

I have 3GiB of RAM and a 17.5GiB swap partition, which shares an extended partition with the root. The other partitions on that drive are a Windows 7 partition that I occasionally use, and the boot partition. I have /home on a separate drive, and this is where most of my apps run from and where data goes, since they're checked out from a repository—I thought my system would run faster that way. Maybe it does, but not when memory swaps!

When I set this system up, I didn't see any indication that an extended swap partition was a bad idea. If this is the problem, is there a way to fix it without having to blow away my OS?

What else should I try?

Thanks,
MikZ.

---

### Post by dabl on 2010-06-24
In addition to tweaking vm.swappiness, you can also [[COLOR="Green"]**tweak**[/COLOR]](http://rudd-o.com/en/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that) the vfs_cache_pressure setting, but in all honesty I don't see your issue as one that can be tweaked away ....

First thing I noticed is, 17G is crazy huge for a swap space, with 3.8G of RAM. I haven't seen a recommendation for more than 1.5X the RAM for years, and lots of people with that much RAM don't even make a swap partition (but I do).  You definitely need a swap space of slightly more than your RAM if you hope to Suspend to RAM (aka "sleep").  But I don't think the memory management functions of a desktop kernel are designed to handle swapping of 4X the RAM -- at least not with a happy user.   :lolflag:

Second, what the heck are you running to consume all that RAM?  The last time I managed to do that, I had to run multiple instances of gnome wave cleaner on audio files, but I'm not sure I would expect that kind of processing to be done on a Lenovo lappy. It almost sounds like you need a server or something.    :-?

Finally, I noted the "... this is where most of my apps run from" -- I do not understand.  Software packages are normally installed in the root filesystem.  Why and how did applications get installed on a different hard drive, or were you only referring to your data?  Could it be possible that the data read/writes through the hard drive bus is the actual culprit, not the swap performance?  Just a thought.

---

### Post by warfacegod on 2010-06-24
Unless you've specifically told the OS to install your apps to the /home directory, they should be in your OS partition.

I agree with dabl, a 17 GB swap is altogether too much. You should consider something more reasonable like around 5 GB or less. I personally haven't used swap in over a year and my system is faster for it.

As far as this 100% RAM use goes, is it RAM use or RAM as cache? There is a difference.

---

### Post by original_MikZ on 2010-06-24
The large swap partition is because I thought I might put in more RAM one day. It's capable of 8GB, so I made I made the swap space twice that, which I know was the recommendation at some point. I'll try reducing the size of my swap partition to 6GB over the weekend and see if that fixes it. Thanks.

As for why I need to much RAM: I'm a web developer, so this pretty much *is* a server, one I can take on the train with me. :) I'm normally running a big Tomcat app with a local DBMS, Eclipse, a whole bunch of unit and load tests, lots of tabs in FireFox, Chrome thrown in for more testing, Selenium on top of both, vim of course, and miscellaneous things like Evolution, Remote Desktop, a music player, etc. It adds up.

Cheers,
MikZ.

---

### Post by original_MikZ on 2010-06-24
Oh, in answer to your other questions: I check out everything I'm running, including Java and Python, from our source repository&#8212;this is so I know what I'm running in my dev environment matches what's in production as much as possible. (Version mismatches can make reproducing bugs very difficult!) So Java, Tomcat and MySQL, and even Eclipse, ends up in directories like /home/<me>/<repository>/<blah>/jvm/java-6-sun/bin. FireFox, Evolution, vim and all the little apps are in /usr/bin, of course, which is a different drive, but not the big, busy stuff.

And I'm quite sure it's RAM we're talking about. System Monitor calls it 'Memory and Swap History', and 100% is 3.8GiB, which is how much RAM my system has.

---

### Post by efflandt on 2010-06-24
Actually swap is not used for suspend (low powered RAM), only for hibernate (ie, suspend to disk).  For hibernate your swap partition should equal or exceed RAM, but 17 GB seems like overkill.  For suspend, it should not matter.

What all are you running that uses up 3.8 GB of RAM?  Is something either not freeing up RAM when it closes, or running away?  I am running 64-bit Lucid on an early Athlon64 3200+ (2 GHz, 1024K cache) using less than 400 MB RAM:

```
free -m
             total       used       free     shared    buffers     cached
Mem:          2009        511       1498          0         21        156
-/+ buffers/cache:        333       1676
Swap:         2236        162       2074
```

---

### Post by dabl on 2010-06-25
> **efflandt said:**
> Actually swap is not used for suspend (low powered RAM), only for hibernate (ie, suspend to disk).

Yep, that is true -- my bad, I was thinking of S2Disk but wrote it wrong.  Thanks.

My rig has 4G of RAM.  A large Win 7 VM, which I allotted 2G, will suck up half of it when I'm using it, and of course running youtube videos in the browser will use a bit too.  I have a 2G swap partition. As long as I am careful to shutdown the VM or anything like that, I can S2Disk with no issues.

Remember, swapping to hard disk was always a low-performance work-around for the problem of insufficient memory -- designed in the days of very expensive 32K memory modules.  It's never going to be a pleasing way to run desktop applications.  I believe an investment in another 4G of RAM as you intended, plus reducing the swap partition to 6G, will make a lot of this problem go away.  Make sure the new DIMMs are fast enough for your CPU and you should be in good shape.

---

### Post by philinux on 2010-06-25
[https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?](https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?)

OP sounds like he needs to run top when things are going bad. Could be a java applet, there is a bug re this. [https://bugs.launchpad.net/openjdk/+bug/551328](https://bugs.launchpad.net/openjdk/+bug/551328) 

When this happens to me memory goes up too. Have to kill java.

```
top
```

See if anything is maxing out. Also install htop and run that.

---

