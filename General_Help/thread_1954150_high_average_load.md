---
title: "high average load"
date: 2012-04-07
forum: General Help
---

### Post by carolinason on 2012-04-07
my load numbers are rarely under one, sometimes they are as high as two. i'm usually just running the web browser, file manager and gedit. is there was to control average load?

---

### Post by soryu on 2012-07-04
i'm at 2.04 
browser,transmission,audacious.
is this a high load???:confused:
lately precise has been freezing(screen) music still plays and programs continue.
sometimes it logs me out.

---

### Post by Doug S on 2012-07-05
Yes, there an issue with current kernels such that under specific conditions reported load averages can be in error too high. A fix is ready and tested, and will shortly start to propagate into the upstream kernels, starting with a future 3.5 release candidate (hopefully the next one). I do not know how long the fix will take to migrate to the other kernel series.
A long term (15 minute time constant) reported load of 2 might be an actual load of 0.5, worst case.
As for things freezing and logging you out, I have no comment nor have I experienced such things on my 12.04 test computers.
 
References:
[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/838811]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/838811")
[https://bugs.launchpad.net/xubuntu-desktop/+bug/985661](https://bugs.launchpad.net/xubuntu-desktop/+bug/985661)
[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/995284]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/995284")
[http://www.smythies.com/~doug/networ...erage/new.html]("http://www.smythies.com/~doug/network/load_average/new.html")

---

