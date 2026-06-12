---
title: "Cannot run out of memory"
date: 2011-09-29
forum: General Help
---

### Post by Meneth on 2011-09-29
I have a netbook on which I've installed Ubuntu 10.10. For the most part it works fine, although I wish it would remember the "Wireless:Off" setting after Suspend.

I don't have a swap partition. I figured that swap only slows things down, and if you don't have enough memory to run a program, it'll exit or crash, and you can free up some memory and try again.

That theory works well on my Windows desktops, but on Ubuntu, when the system is almost out of memory, the hard drive becomes hyperactive, and the computer slows to a crawl, and no program reports "out of memory". If I'm lucky, I can get to a console and 'killall' something, but often, I have to hold the power button to force a cold reboot, which does neither my patience or filesystem any good.

Does anyone know what's going on here?

Is the system swapping, despite my instructions that it shouldn't?

Is the system reading a bunch of files from the hard drive all the time, and relying on a certain amount of disk cache being available? If so, it it possible to force the system to maintain a certain cache size rather than give it away to programs?

---

### Post by dino99 on 2011-09-29
yeah, linux swap if it needs, even without swap partition, because it will do it inside a /home/file. By default your system might have a swap partition, that is only used when 90 % of ram used, linux load app/lib into ram as much as it need to work quicker. This setting can be tweaked with swappiness.

standard install:
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

on low ram system Lubuntu or xubuntu run better

---

### Post by Meneth on 2011-09-30
I see. My system's swappiness is set to 0. Perhaps that's why the slowdown appears so suddenly.

I want to disable swap completely. I want malloc() to return NULL. How do I make that happen?

---

### Post by 2F4U on 2011-09-30
Just found an interesting discussion about swappiness here:

[http://kerneltrap.org/node/3000](http://kerneltrap.org/node/3000)

It may help to understand the various approaches.

---

### Post by cavbleu on 2011-09-30
I had the same problem and my desktop, under Ubuntu 11.04 and 11.10, always run out of memory. I tried all possible optimization and tuning and I still have the same issue.
One day I tried the 200 lines kernel patch [http://bit.ly/eCyATL](http://bit.ly/eCyATL) and my machine becomes finally decent.
I don't know if it will work for you but give it a try.

---

### Post by deserthowler on 2011-09-30
I have a swap partition but seldom use it.  It's there just in case.  Once in a while I do manage to use it.  Linux swap is nothing like Windows.  Sometimes I run for days without hitting swap file.

Earl

---

### Post by wildmanne39 on 2011-10-01
Hi, also ubuntu is using the ram to cache to your system so it will run faster and it will empty the ram as needed to allow room for other programs that need it.

If you do not have enough swap or it is not installed then that maybe the problem.

How much ram do you have installed?

Have your ran 
```
free -m
```
in the terminal to see how much is cached? because cached is still available when needed.

You may want to run top in the terminal also and see how much cpu is being used and what is using it.

You may have something strange going on hopefully top will show something that looks like it is using up most of the ram so you can isolate the problem.
Thank you

---

