---
title: "Installing Ubuntu from USB"
date: 2010-12-20
forum: General Help
---

### Post by BKbroila on 2010-12-20
I've tried Ubuntu from a live USB already and liked it, so I'm currently trying to get the ISO burned onto another flash drive. However, I can't get it working. 
My laptop has an Intel Core Duo 2 P8600. I thought I had i386 architecture, but during the process of making the USB, the program only recognizes the ISO file if I select the AMD64 distribution. 
So do I have i386 or AMD64??? I asked a friend and he said that I had i386 and could run AMD64, but told me to go with i386. 
Thanks

---

### Post by 0N3 on 2010-12-20
[http://www.youtube.com/watch?v=iDr-rnz1WTQ](http://www.youtube.com/watch?v=iDr-rnz1WTQ)

---

### Post by sikander3786 on 2010-12-20
Intel Core 2 Duo is 64-bit capable so you can install either the 32-bit version or the 64-bit version i.e, i386 or AMD64 whichever you prefer.

Why the 64-bit is named AMD64 is because AMD got the 64 bit technology a touch before Intel got there. But it runs on all the 64-bit capable machines whether Intel or AMD ;-)

Feel free to ask if you need any help regarding the install :-)

---

### Post by BKbroila on 2010-12-20
> **sikander3786 said:**
> Intel Core 2 Duo is 64-bit capable so you can install either the 32-bit version or the 64-bit version i.e, i386 or AMD64 whichever you prefer.

Why the 64-bit is named AMD64 is because AMD got the 64 bit technology a touch before Intel got there. But it runs on all the 64-bit capable machines whether Intel or AMD ;-)

Feel free to ask if you need any help regarding the install :-)

Thanks for the tips. So would telling Ubuntu that I have i386 or AMD64 be better? Is there a difference in the functionalities if I were to do i386 compared to AMD64?

---

### Post by sikander3786 on 2010-12-20
32-bit vs 64-bit is a very extensive topic and you need to Google that and gather some info.

In short, 64-bit supports RAM > 3 GB natively while 32-bit can also support that nowadays by using a PAE-Kernel so that advantage is no more an advantage.

64-bit is faster while doing some data compression, video encoding tasks as compared to 32-bit as it utilizes the resources more efficiently.

While doing the routine tasks, you might not even feel the difference.

There were a few problems with flash previously while considering 64-bit but no more there I believe. I'm using 64-bit my self.

I know I am missing many of the things here :-)

And if you want to go the safer route, burn 2 different Live CDs of both 32-bit and 64-bit. Try them from the disc and test all your hardware with both of them. There have been reports that some hardware drivers for 64-bit devices were missing in 32-bit versions. Check it yourself and install the one that performs better.

At last, either 32-bit or 64-bit OS can be installed to a 64-bit capable system. But 64-bit OS can never installed to a 32-bit system.

Hope that makes some sense :-)

---

### Post by BKbroila on 2010-12-20
Oh wow. I feel like an idiot. I thought i386 was a different type of 64-bit architecture...
Sorry for wasting your times guys!

-----------------EDIT---------------------------------------------

I just tried installing Ubuntu, and ended up completely wasting my time.
What happened was that I had about 140 GB of unallocated space left untouched. I wanted to install Ubuntu on 80GB of it (20 GB to the '/' partition and 60GB to the '/home' partition. From what I remember, when I clicked on the unallocated space, there was no option to format the space. So I randomly clicked Revert, since it was the only option, and that ended up in a complete wipe of my HDD....
So should I partition my hard drive and make an 80gb section of NFTS while I'm in Windows? If that's what I should do, would the option "Resize IDE1 master, partition #1 (hda1) and use freed space" come up for that partition?
Thanks

---

