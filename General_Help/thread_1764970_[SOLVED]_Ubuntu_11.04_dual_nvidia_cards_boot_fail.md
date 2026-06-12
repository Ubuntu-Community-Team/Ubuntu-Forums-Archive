---
title: "[SOLVED] Ubuntu 11.04 dual nvidia cards boot fail"
date: 2011-05-22
forum: General Help
---

### Post by Dans564 on 2011-05-22
hey everyone,

I'm writing this in attempt to save some1 some trouble cause I was stuck on this for about 2 weeks.

Ok so ubuntu 11.04 would work fine until I installed the proprietary drivers, then the system wouldn't even boot.  During the boot process the screen would blink a couple of times and it would just hang after saying it loaded GDM (although gdm never actually appeared).  I was however always able to boot into failsafeX from grub.  

SOLUTION:

I figured out that adding vmalloc=256MB to my grub config fixed the problem!
Here is a link describing how to do so: [http://www.warp1337.com/content/ubuntu-1104-natty-segmentation-fault-nvidia-geforce-9-series-kernel-failure-solved](http://www.warp1337.com/content/ubuntu-1104-natty-segmentation-fault-nvidia-geforce-9-series-kernel-failure-solved)

Hope this helps some1 cause it helped me a lot.


-Dan

---

