---
title: "High memory usage or faulty memory?"
date: 2009-07-02
forum: General Help
---

### Post by goanga on 2009-07-02
I've noticed a significant slow-down in my laptop's performance lately and I do believe it's due to very high memory usage and, consequently, swap usage which, combined with a fairly slow hard-drive, makes the laptop, at times, unresponsive.
So I investigated.
I have a Dell Inspiron 6400 with 1 GB of RAM.
It seems that the memory usage is at 95%+ constantly (970-980 out of 993 MB), with not much running; also, the high usage seems unaccounted for. Looking at top, the amount memory used by the processes just doesn't add up: opera uses some 10-20%, Xorg some 6-7%, compiz 2% and the rest are 1% or less.
So I rebooted and when getting to the Gnome welcome screen, I changed terminal and logged in to a CLI session. When looking at free and top, I saw that the memory usage was about 850MB, with no GUI or programs running, just the usual services.
I do have apache and mysql running in the background, but after stopping them, the memory usage remained essentialy the same.
On the other hand, on my girlfriend's laptop, which has only 512MB of RAM, when doing the same thing, the used memory is only about 250MB, which seems about right.

Now. If anybody made it this far: is it possible that the memory is faulty or should I just look for memory leaks?

I did try memtest86 but, while I wasn't able to wait for the final result, at about 60% of tests done, it showed no errors.

HALP!

---

### Post by triangleSLO on 2009-07-02
These are my results with Firefox and ordinary stuff running in the background.
```
blaz@modell:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3015        726       2288          0         22        341
-/+ buffers/cache:        362       2653
Swap:         6534          0       6534

``` 

Leave memtest running through the night if nothing shows up your memory is probably ok

---

### Post by goanga on 2009-07-02
Well, your Gnome session + Firefox + background programs = 726 MB
My CLI session + nothing = 850.

Does not compute :D

---

### Post by triangleSLO on 2009-07-02
My CLI session is 670 MB.

---

