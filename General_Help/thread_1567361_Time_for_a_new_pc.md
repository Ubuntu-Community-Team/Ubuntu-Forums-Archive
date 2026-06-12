---
title: "Time for a new pc?"
date: 2010-09-03
forum: General Help
---

### Post by PaulM1985 on 2010-09-03
Hi

I have been having trouble with my pc.  It just shuts down randomly and has occurred quite often recently.  Only managing to stay on for about ten minutes.  I think it is either motherboard, graphics card or power supply.  I have lots of deadlines coming up and plenty to do. Are there any obvious things I can check? 

Paul

---

### Post by gldearman on 2010-09-03
Is it just spontaneously losing power and going black, or is Ubuntu going through an emergency shutdown?

If the former, that certainly sounds like a power supply issue.  Do you have a voltmeter?  A replacement power supply would be inexpensive, if that were the problem.

Try disabling the video card, restarting, and seeing if the problem persists.  That could pinpoint or eliminate the card as the source of your problem.

When I was having spontaneous shutdown issues it was the CPU overheating.   Make sure the inside of the PC is clean and dust-free, all the fans are working, and the PC (I'm writing this assuming a desktop) gets good airflow.  Also, you can monitor your CPU temperature from the desktop with the computertemp panel applet, available in the repos.

Hope something here helps!

---

### Post by uRock on 2010-09-03
Is it overheating? If it has censors, then there are a few programs in the Ubuntu Software Center that will help with monitoring.

Also, there is a hardware testing application. System> Administration> System Testing

---

### Post by rocknrollmouse on 2010-09-03
Random shutdowns of the type you discribe usually tend to come from overheating or memory faults.  The easyest to check for is memory; using a live disk boot to memtest and let it run through its checks, any errors are clearly shown(!).

Checking for overheating is more tricky, but one of the safe things you can do is check your bios.  As well as heat monitoring, some bios keep logs of "events" such as overheating & shutdowns.

---

