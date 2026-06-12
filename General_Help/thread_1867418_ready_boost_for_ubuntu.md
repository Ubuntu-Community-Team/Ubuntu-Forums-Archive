---
title: "ready boost for ubuntu?"
date: 2011-10-22
forum: General Help
---

### Post by serpentracer on 2011-10-22
windows has a ready boost option to use a thumbdrive to help speed up a slower computer does ubuntu 11.10 have anything like this?
I seen a sticky from 2007 but that was a long time ago and the commands in that thread do not work.

---

### Post by wolfen69 on 2011-10-22
I don't believe it exists. At least I've never heard of it. Make sure you have plenty of RAM and you won't have to worry about it.

---

### Post by haqking on 2011-10-22
> **serpentracer said:**
> windows has a ready boost option to use a thumbdrive to help speed up a slower computer does ubuntu 11.10 have anything like this?
I seen a sticky from 2007 but that was a long time ago and the commands in that thread do not work.

readyboost is really just another swap.

it is debatable these days as to if you need swap, if you look at your memory resources and it is hitting the limit either increase physical memory or use actual swap from the HDD.

or use a swapfile

if you really wanted to you could use a USB or SD card with swapon but i doubt you will get any performance increase

---

### Post by serpentracer on 2011-11-01
yeah that's the problem, this old laptop is already at it's max of 1 gig.  I like to use it for tinkering and wondered about using my thumb drive for some extra ram.
been reading about some people feel it's useless and others say it performed a miracle resurrection on their's.
seen a few other sites say linux doesn't need it because it uses the memory etc much better than windows.

---

### Post by Rodney9 on 2011-11-01
Use a light weight operating system like [Lubuntu]("https://wiki.ubuntu.com/Lubuntu")

---

### Post by Slim Odds on 2011-11-01
> **haqking said:**
> [SIZE=3][COLOR=Red]readyboost is really just another swap.[/COLOR][/SIZE]

it is debatable these days as to if you need swap, if you look at your memory resources and it is hitting the limit either increase physical memory or use actual swap from the HDD.

or use a swapfile

if you really wanted to you could use a USB or SD card with swapon but i doubt you will get any performance increase

That is most definitely wrong. Readyboost is much more comparable to cache.

Windows moves more frequently used files to the flash drive for faster access than using the spinning hard drive.

I've tried it on my laptop and didn't notice much of a difference. It seemed to spend way too much time updating the flash card.

---

### Post by haqking on 2011-11-01
> **Slim Odds said:**
> That is most definitely wrong. Readyboost is much more comparable to cache.

Windows moves more frequently used files to the flash drive for faster access than using the spinning hard drive.

I've tried it on my laptop and didn't notice much of a difference. It seemed to spend way too much time updating the flash card.

I meant it more as in to implement it under Linux as it does not directly support the readyboost technology, hence the mention of a swap file or usage of the USB or SD for that purpose.

[http://www.comptalks.com/ready-boost-in-linux/](http://www.comptalks.com/ready-boost-in-linux/)

---

### Post by serpentracer on 2011-11-01
> **Rodney9 said:**
> Use a light weight operating system like [Lubuntu]("https://wiki.ubuntu.com/Lubuntu")

yeah I might try that.
what sucks is it's a pentium 4 with a 2.4ghz processor but only 1 gig of ram.  oh and a terrible graphics processor.  I think it's called amd pos..lol
naa it's a ati mobility radeon 4x agp with 3D architecture.  (my bottle neck).

---

### Post by Slim Odds on 2011-11-01
> **haqking said:**
> I meant it more as in to implement it under Linux as it does not directly support the readyboost technology, hence the mention of a swap file or usage of the USB or SD for that purpose.

[http://www.comptalks.com/ready-boost-in-linux/](http://www.comptalks.com/ready-boost-in-linux/)

It's **nothing** like swap at all. That's all.

P.S. The guy who wrote that article does not know what he's talking about.

---

### Post by Mark Phelps on 2011-11-02
I tried ReadyBoost on a laptop with 1GB of memory (using Windows) and it didn't appear to accomplish anything useful, in fact, as someone else mentioned, it seemed to slow it down writing to the USB stick.

So, it's probably a GOOD thing that we don't have ReadyBoost.

---

### Post by Redcard on 2011-11-02
I was talking at one time to a microsoft guy about ReadyBoost.  He laughed and said it was helpful, but most the effects are placebo in nature.

---

### Post by 3rdalbum on 2011-11-02
Real RAM runs extremely fast; DDR2 and DDR3 data rates are really huge.

SATA, which is how your hard disks connect to the computer, is pretty fast but nowhere near what DDR2 can accomplish.

USB 2, which is how your flash drive connects, is a mere fraction of SATA's speed. It's a mere drip compared to the viscous stream of DDR2.

There's no way can Readyboost actually help. Why place a cache on a disk that's connected via a very slow bus? Better off putting the cache in a continuous block on the regular HDD.

Besides, Vista requires so much RAM compared to Ubuntu, that your low-RAM Ubuntu machine with no Readyboost would still run faster than Vista or 7 with Readyboost.

---

### Post by Slim Odds on 2011-11-02
The only benefit of the flash drive in these cases is the seek time. Pretty much zero for flash, but can be sometimes quite large for any spinning disk.

That's why it's hard to compare the two sometimes.

---

### Post by killermist on 2011-11-03
Where a flash drive would provide a "boost" to system performance would be to keep "frequently accessed" files where access time is significantly faster than the speed of a hard drive.

There are downsides to this.
Flash drives have a SLOW write rate.  This may not be immediately noticeable for short writes because caching mitigates the delays.  But getting into large numbers or volume of write the true speed of writing to USB flash is painfully apparent.
Anything important (and basically everything has to be treated as important) that gets written to the flash also has to be written sooner or later to the hard drive anyway.  Any power failure before the data is pushed from flash to HDD is lost without some recovery system on the next boot to make sure flash content is pushed to HDD.

All that said, to implement this would be "very hard" at best, and that's if you have programmers actually interested in the (arguably) trivial gains.

As others have said, more memory and better tuned (or just more) memory based caching would do even better.

---

### Post by kurt18947 on 2011-11-03
> **serpentracer said:**
> yeah that's the problem, this old laptop is already at it's max of 1 gig.  I like to use it for tinkering and wondered about using my thumb drive for some extra ram.
been reading about some people feel it's useless and others say it performed a miracle resurrection on their's.
seen a few other sites say linux doesn't need it because it uses the memory etc much better than windows.

Here are a couple things you could do to determine of extra RAM might be helpful.  Run the following command in a terminal:  "free -m"  or open "system monitor".  "system monitor" location varies by distro. If using system monitor bear in mind that system monitor uses some RAM itself. See if swap is being used and if so, how much.  Unless you have a memory intensive or several applications open, Ubuntu doesn't really require that much RAM. If you want to add RAM to an older system and new RAM is pretty expensive -which it can be for out-of-production systems - you might check auction sites.  I bought a DIMM for a vintage notebook (brought it up to a capacious 512 MB. :P) for < $10.  Install it and immediately run memtest on it.  Be sure the seller offers return/exchange if the test fails.

---

### Post by mightyiam on 2013-03-03
There's a solution in Ubuntu. It is called flashcache. Here's [how I did it]("http://randomcrystal.blogspot.co.il/2013/03/hybrid-ssdhdd-ssd-caching-using.html") in my blog.

---

### Post by oldos2er on 2013-03-03
Old thread closed.

---

