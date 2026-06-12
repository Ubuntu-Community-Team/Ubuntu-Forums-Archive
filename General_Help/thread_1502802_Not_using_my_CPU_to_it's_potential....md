---
title: "Not using my CPU to it's potential..."
date: 2010-06-06
forum: General Help
---

### Post by d00derino on 2010-06-06
When I loaded Ubuntu on my machine, I noticed it was slower than when I had Windows. It hit me, and a quick cat /proc/cpuinfo showed that my processor was running at 1gHz, when it should be running at 2! 

Why doesn't Ubuntu want to use half of the CPU speed? I can't figure it out!

---

### Post by sdennie on 2010-06-06
If you look at /proc/cpuinfo you will find the speed the CPU is currently running at.  Most of the time, that will be the lowest speed your CPU can run at because, most of the time, your machine is idle.

I don't know why you'd find Ubuntu to be slower than Windows but, /proc/cpuinfo isn't giving you a hint to the answer.

---

### Post by 3rdalbum on 2010-06-06
> **d00derino said:**
> When I loaded Ubuntu on my machine, I noticed it was slower than when I had Windows. It hit me, and a quick cat /proc/cpuinfo showed that my processor was running at 1gHz, when it should be running at 2!

cat /proc/cpuinfo reports whatever speed the CPU is currently running at. All modern CPUs run at a lower speed when they are at near-idle, to save power. They jump to full performance when under load.

Add the CPU Frequency Monitor to your panel and it will always tell you exactly what speed or what percentage your CPU is running at, at any particular time. You can also change the speed or change the 'governor' (the method used to govern the speed of the CPU); make sure that the governor is set to 'OnDemand' for best results.

---

