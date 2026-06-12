---
title: "viewing pictures causes GPU to overheat"
date: 2009-08-14
forum: General Help
---

### Post by eival on 2009-08-14
any time i use the default Gnome image viewer either in full screen or windowed i can hear my fan start running an then after a few minutes it gets louder, i can see the temp rising while viewing the NVIDIA control panel's thermal monitor, it will continue to increase in temp well into the red which is 100 degrees.

for the past year i had been using the default driver in the repositories an didnt realise it hadnt updated so i installed the latest from NVIDIA about a week ago, i hoped that this would of fixed my issue but after a week its still happening.

i dont know alot about GPU's but heres some of my specs, if you need anything else just ask.

[http://i31.tinypic.com/28ithxd.png](http://i31.tinypic.com/28ithxd.png)

[http://i25.tinypic.com/nmxdo2.png](http://i25.tinypic.com/nmxdo2.png)

[http://i25.tinypic.com/s4yu8o.png](http://i25.tinypic.com/s4yu8o.png)

im running on Ubuntu 8.04

i think the Adaptive Clocking might be the issue cause its the only setting i see that i cant change, is there a way to manually turn it off, or make it run at level 0,1,2 all the time? what would the pros/cons be?

thanks.

---

### Post by jeb800e on 2009-08-14
I'm no expert, but I think it may be the driver causing this problem. Look for a newer version of the driver or uninstall it, if possible. I installed the driver for my ATI Radeon Graphics card, and I disliked it so much, I had to remove it and use the plug & play features of Linux.

---

### Post by eival on 2009-08-14
> **jeb800e said:**
> I'm no expert, but I think it may be the driver causing this problem. Look for a newer version of the driver or uninstall it, if possible. I installed the driver for my ATI Radeon Graphics card, and I disliked it so much, I had to remove it and use the plug & play features of Linux.

i did update to the latest one an its still having the same issues as the old driver in the Ubuntu repositories, so im thinking its something else.

also it doesnt overheat when watching dvdrips windowed or fullscreen, its only with pictures, even if its something very small in size. idk if that could help pinpoint the problem.

---

