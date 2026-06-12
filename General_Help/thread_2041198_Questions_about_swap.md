---
title: "Questions about swap"
date: 2012-08-12
forum: General Help
---

### Post by najdorfchess on 2012-08-12
Hi all. I'm not a trivial user but I had this big question about swap when I was reinstalling ubuntu on my laptop this evening. Is swap really necessary? My laptop has 8GB of RAM and I really don't need hibernation at all and I don't run heavy applications except maybe for MATLAB! 
So I decided to not allocate any swap partition and installed my OS and it's been working quite alright till now (for the past 3 hours). So I wanted to ask the pros what swap really does (listing all functions apart from being physical memory which I already know) and whether it's really required or not. A very detailed discussion would be nice. 
I'm guessing there will be posts in the past on the topic and links to those would also be very helpful. Thanks :)

---

### Post by chadk5utc on 2012-08-12
I also have 8Gigs and hardly use either it through a fit with out a swap file so I added a small one I think even under load my mem usage has never been higher than about 8% there are lots of articles on this heres one:   (explains more than I could)
[https://www.linux.com/news/software/applications/8208-all-about-linux-swap-space/](https://www.linux.com/news/software/applications/8208-all-about-linux-swap-space/)

---

### Post by asmoore82 on 2012-08-12
The explanation I heard a very long time ago which might not have even been correct and even if might no longer be correct is that if and when a running kernel reaches the out of memory condition and absolutely no swap is allocated it may be a crash/deadlock scenario. 

So in other words, if you have no swap and somehow fill your RAM, you're not allowed to complain if Linux dies on you. For this reason I keep just 512 MB of "token" swap.

I, too, would be interested in a more "authoritative" definite answer.

---

### Post by CaptainMark on 2012-08-12
As above I would recommend keeping a token amount of swap because if a program does decide to attempt to write to swap even if your memory buffer isn't full then you'll have problems. I have half the memory you do and even that will probably never really require swap writes but just incase I keep 1gb for swap, it's not like you'll miss that 1gb of hdd space with modern drives being so large

---

### Post by najdorfchess on 2012-08-12
Thank you all for the overwhelming replies in quick time. So I will add 'token' 1gb of swap space to my Ubuntu 12.04 64-bit. 
I guess I would use gparted to do that. Any specific suggestions on this front?

---

### Post by jroa on 2012-08-12
I have 3GB of ram on my current install and I allocated 6GB of swap space.  I was curious about how many programs need to be running before swap is used, so I opened a bunch of programs and checked the swap usage after opening each one.  I had about 10 things running at once before I saw any swap usage, and then even, it was only a small amount and I still had a lot of ram left.

With 8GB, you will probably be fine with out swap.  Just my opinion, though.

---

### Post by najdorfchess on 2012-08-12
Two very good points about "necessity" of swap as if potentially RAM runs out (a crazy matlab code can cause that) my system could die. So good to have swap handy. I roughly know about the architecture of how the OS is being formed it's file structure and stuffs but haven't really looked deep into the OS (not even once) and would definitely need to do sometime to understand issues like these. Also the application writing to swap, I'm curious which application might actually do that? Even if they did, wouldn't they have exception handlers in place for space conservists like me?!

---

### Post by Elfy on 2012-08-12
You could if you wanted use a swap file instead of swap partition. 

[https://help.ubuntu.com/community/SwapFaq/#How_do_I_add_more_swap.3F](https://help.ubuntu.com/community/SwapFaq/#How_do_I_add_more_swap.3F)

---

### Post by oldos2er on 2012-08-12
I have 8GB RAM too. Rather than use a swap partition, I just have a 512MB swap file (see [https://help.ubuntu.com/community/SwapFaq/](https://help.ubuntu.com/community/SwapFaq/) for a how-to). I don't think the system's ever touched it.

---

### Post by najdorfchess on 2012-08-12
That was helpful. I did create a swap file of 1GB just in case so that nothing happens. The swapfaq was helpful but most of the stuffs are things I already know I do wanna know more. 
For now marking this thread as solved! Thanks everyone :)

---

### Post by asmoore82 on 2012-08-12
After thinking it through for my post, I think I'm going to switch to a swapfile from now on too. I heard that a swap partition always at the end of the physical hard drive was important to increase performance way back in the day because those old drives could seek to the end faster than they could seek to some specific midpoint with accuracy. A professor once told us to think of the movement of the drive heads not as just an act of moving, but instead as the act of accelerating and decelerating. In this case, when you have farthest to go, you can reach a higher top speed.

I doubt this would matter much any more and not at all for SSD drives. And it would make swap more reconfigurable and partitioning simpler.

---

### Post by najdorfchess on 2012-08-12
Indeed! In today's 'good' hardware swap isn't a big necessity, so swap file should work.

---

