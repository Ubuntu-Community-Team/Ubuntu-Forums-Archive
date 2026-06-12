---
title: "CPU usage in System Monitor, not Hardware Monitor"
date: 2010-11-02
forum: General Help
---

### Post by uriel1998 on 2010-11-02
I'm a relative Ubuntu noob, so this is probably something stupid I missed... but I'm not finding anything that addresses this.

I had been running Folding@Home as a distinct process when I was running Windows - I'd manually start and stop it.  (This was intentional.)  I just installed it on my Ubuntu 10.04 install, and it's running just fine.

The only thing that's strange is that while [FONT=Courier New]top [FONT=Verdana]and the System Monitor report the CPU usage correctly, the Hardware Monitor applet (1.4.2) isn't reporting the usage at all.[/FONT][/FONT]

As I said, it's an annoyance, nothing more - the applet reports other CPU usage accurately, and Folding@Home runs smoothly and perfectly.

[Solution:  Gnome's Hardware Monitor applet (1.4.2), the one with "curves" and "flames", apparently displays both "user" and "system" processes.  Processes marked "nice" (that is, only running when the machine is idle) do not appear as CPU usage.  They do appear as CPU usage in the System Monitor applet.

---

### Post by Chris_82 on 2010-11-07
Same here, I have at least one process that is not seen by hardware monitor 1.4.2: **update-apt-xapian-index**

It uses up to 95% on my machine but the monitor shows about 2%.
I have found no bug report on that so it might be necessary..
(By the way, the graphed network throughput is always too high..)

cheers.

---

### Post by 3Miro on 2010-11-07
You mean the System Monitor applet, the Hardware Monitor one is for temperature and voltage and such. On the properties for the applet, are you looking at the CPU monitor or the System Load measurement.

Also, for the network speed, a program like a Transmission will measure internet traffic in terms of "useful" information. Every time you send or get something on a network you send/get more than that. The applet has no way of distinguishing what is considered "useful" and what is meta data, so it reports total network transfer.

---

### Post by Chris_82 on 2010-11-07
> **3Miro said:**
> You mean the System Monitor applet, the Hardware Monitor one is for temperature and voltage and such.

I mean the gnome applet called [hardware-monitor]("https://launchpad.net/ubuntu/+source/hardware-monitor").

> On the properties for the applet, are you looking at the CPU monitor or the System Load measurement.
I chose CPU usage, not the average system load.

> Every time you send or get something on a network you send/get more than that.
Yep that makes perfectly sense, I guess I got up too early this morning :).

---

### Post by uriel1998 on 2010-11-07
> **3Miro said:**
> You mean the System Monitor applet, the Hardware Monitor one is for temperature and voltage and such. On the properties for the applet, are you looking at the CPU monitor or the System Load measurement.

Actually, I *did* mean Hardware Monitor applet - at least in 1.4.2 (from 10.04 stock Ubuntu install), there's the ability to graph (and present in more ways)  the things that the System Monitor applet can show.  It's what I came across first.  I was using Hardware Monitor to graph CPU -> All Processors.  

The System Monitor applet seems to have the answer.  The Folding@Home process shows up there - but only under "Nice".  The Hardware Monitor applet only shows "System" and "User" processes, not "Nice" or "IOWait".

Now if I could just combine all the functions and options of the System Monitor and Hardware Monitor applets...

---

