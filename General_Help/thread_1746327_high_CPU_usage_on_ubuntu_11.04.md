---
title: "high CPU usage on ubuntu 11.04"
date: 2011-05-01
forum: General Help
---

### Post by jajaja_622 on 2011-05-01
I just installed ubuntu 11.04 on my machine, an hp dm4 with core i5-430m, 4 GB ram and intel hd graphics.
The problem is that the cpu usage on system monitor is really high (60 plus % on at least 2 cores) and i'm not doing anything. Any ideas on what might be causing this problem? Looking at the task manager firefox-bin uses 38% CPU  and gnome-system-monitor 44% CPU

Pd: i allready tried loging in classical ubuntu but the problem persist

**Update**: The reason of high CPU usage was the gnome-system-monitor, if you have the same problem try using ´top´ on the terminal instead.

---

### Post by gordintoronto on 2011-05-01
Is there a way to install the CPU Frequency Monitor applet? If your CPU is running at 200 MHz, 44% CPU is not all that much. (My CPU runs at 2100 MHz when it is busy, but spends most of its time at 800 MHz. The i5 might go lower.)

---

### Post by lovinglinux on 2011-05-01
Install [Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/433/") and [AdBlockPus]("https://addons.mozilla.org/en-US/firefox/addon/1865/") in Firefox. This will reduce CPU usage, because it won't load unnecessary contents like flash stuff and ads. Flash is most likely to be the culprit.

---

### Post by jajaja_622 on 2011-05-02
I kind of solved it.. I mean, firefox was in part the culprit so i downloaded Opera, but the fans still where max on. It turns out that gnome-system-monitor was the one eating all the resources.
I opened the terminal and typed top, I'm not sure but i think it has the same functionality of system monitor but without the graphical UI. It confirmed that what was taking all my resources was gnome-system-monitor, so i closed and now everything its fine.

---

### Post by timmans on 2011-05-02
I am having the same problem but it is not being caused by Firefox...

According to htop the problem process is
/usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-s9jXwK/database -nolisten tcp

This appears to be the X Server and currently this process is using up 85-90% of one core in either gnome or unity, even with nothing open.  

Had no problems with 10.10 beforehand so its something to do with the fresh install of 11.04. Any ideas?

---

### Post by lovinglinux on 2011-05-02
> **timmans said:**
> I am having the same problem but it is not being caused by Firefox...

According to htop the problem process is
/usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-s9jXwK/database -nolisten tcp

This appears to be the X Server and currently this process is using up 85-90% of one core in either gnome or unity, even with nothing open.  

Had no problems with 10.10 beforehand so its something to do with the fresh install of 11.04. Any ideas?

Make sure you have the latest video drivers installed.

---

### Post by jajaja_622 on 2011-05-02
> **timmans said:**
> I am having the same problem but it is not being caused by Firefox...

According to htop the problem process is
/usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-s9jXwK/database -nolisten tcp

This appears to be the X Server and currently this process is using up 85-90% of one core in either gnome or unity, even with nothing open.  

Had no problems with 10.10 beforehand so its something to do with the fresh install of 11.04. Any ideas?

As i said before the problem was the gnome-system-monitor, it doesnt sound your problem is the same btw.. maybe you should try logging out and back in, but with the classical desktop, just to know if Unity is the problem.

---

### Post by timmans on 2011-05-02
> **lovinglinux said:**
> Make sure you have the latest video drivers installed.

Spot on! Was using NVidia driver 173 for some reason. Upgraded to the latest and CPU is back to less than 10%. 

Thanks!

---

### Post by asadmalik on 2011-05-03
I am facing the same problem of high CPU usage in 11.04
The System Monitor shows-
CPU1: 35% & CPU2: 100%
with no application running.

Earlier, with 10.10 my CPU usage was
CPU1: 8%  & CPU2: 6~7%

Processor-E700@3.2GHz
Graphic Card- ATI Radeon HD4850 and I have the latest ATI drivers installed.

---

### Post by lovinglinux on 2011-05-03
> **asadmalik said:**
> I am facing the same problem of high CPU usage in 11.04
The System Monitor shows-
CPU1: 35% & CPU2: 100%
with no application running.

Earlier, with 10.10 my CPU usage was
CPU1: 8%  & CPU2: 6~7%

Processor-E700@3.2GHz
Graphic Card- ATI Radeon HD4850 and I have the latest ATI drivers installed.

The system monitor uses too much CPU. Use "top" on a terminal instead.

---

### Post by layr on 2011-05-03
Same here. CPU usage is 3-6% higher than in Meerkat. Also, GPU temp idles 3-5 degrees higher.

---

### Post by asadmalik on 2011-05-03
> **lovinglinux said:**
> The system monitor uses too much CPU. Use "top" on a terminal instead.

thanks. it shows normal usage in terminal:D

---

### Post by stefanokan on 2011-05-05
I discovered in my system that the Canon printer driver is using 98% of the cpu. May be a bug of the driver or more probably an incompatibility with the last kernel.

---

### Post by mykrob on 2011-05-06
I noted that Flash seems to spike CPU usage quite often to 100%, whereas this didn't happen in Maverick, or in Windows 7. I can duplicate the problem in Chrome or Firefox, and it literally only happens when Flash video is playing.

Wish I could figure out this one...

---

### Post by mykrob on 2011-06-02
Still havign the same problem, wonder if anyone has any fixes for this for users with Intel graphics. The same issue was not present for me on any previous version of Ubuntu.

Thanks,
-myk

---

### Post by vanlindholm on 2011-07-06
> **asadmalik said:**
> I am facing the same problem of high CPU usage in 11.04
The System Monitor shows-
CPU1: 35% & CPU2: 100%
with no application running.

Earlier, with 10.10 my CPU usage was
CPU1: 8%  & CPU2: 6~7%

Processor-E700@3.2GHz
Graphic Card- ATI Radeon HD4850 and I have the latest ATI drivers installed.
I had the same problem on my hp compaq 6710b (4gb ram). I tried various things to fix this (including upgrading the Kernel) but the Xorg process and compiz kept the CPU usage around 60% constantly. In the end the only solution to the problem I found was to switch profile to 'Ubuntu Classic - No effects'. I use gnome-do to search / launch applications in a similar style to unity..

---

### Post by gimspang on 2011-10-16
Same issue:
It happens ONLY when System Monitor is open and on the Resources tab, regardless of being in the foreground or minimised.
I do have a canon driver installed, too (and not working with plenty of bugs), but also I have kernel 3.0.4 compiled to be as interactive as possible and to provide statistics of process usage.
It looks like a lot of resources are used when a program wants to know how much cpu is used by processes.
Maybe kernel config problem?

---

### Post by Cordess on 2011-10-17
The problem does still exist.
Because this thread is marked as "solved", when the problem is not solved, i opened a new thread here:

[http://ubuntuforums.org/showthread.php?t=1863161](http://ubuntuforums.org/showthread.php?t=1863161)

---

### Post by paichkash on 2012-08-22
> **gimspang said:**
> Same issue:
**It happens ONLY when System Monitor is open and on the Resources tab, regardless of being in the foreground or minimised.**
I do have a canon driver installed, too (and not working with plenty of bugs), but also I have kernel 3.0.4 compiled to be as interactive as possible and to provide statistics of process usage.
It looks like a lot of resources are used when a program wants to know how much cpu is used by processes.
Maybe kernel config problem?

yes u r right i also found that fact ..

---

