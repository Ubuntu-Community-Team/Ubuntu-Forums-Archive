---
title: "Won't Come Out of Standby"
date: 2006-02-01
forum: General Help
---

### Post by OPaul on 2006-02-01
Whenever my laptop goes into Standby it will not come back out. I've set the Standby option to 1 min under the Screen saver preferences so I'm sure that it is this option that is causing the problem. I have a Geforce4 420 Go with the 7667 drivers.

---

### Post by o_fortuna on 2006-02-02
[QUOTE=OPaul]Whenever my laptop goes into Standby it will not come back out. I've set the Standby option to 1 min under the Screen saver preferences so I'm sure that it is this option that is causing the problem. I have a Geforce4 420 Go with the 7667 drivers.[/QUOTE]
I'm not sure exactly what the problem is; however, try looking at this [guide]("https://wiki.ubuntu.com/NvidiaLaptopBinaryDriverSuspend?highlight=%28suspend%29") to getting suspend to work with Nvidia drivers. That may be what you need.

You may also have a look at these other articles: [SuspendHowto]("https://wiki.ubuntu.com/SuspendHowto?highlight=%28suspend%29") and [HOWTO: Suspend2 in Breezy]("http://www.ubuntuforums.org/showthread.php?t=75443"). The second one is a suspend-to-disk, so I'm not sure if that's exactly what you need/want, and the first one seems a bit out of date; nonetheless, if the first guide doesn't work for you, you might want to check the others out.

---

### Post by OPaul on 2006-02-02
Well Suspend isn't the problem, it's Standby. Which as far as I know just turns the screen black.

---

### Post by OPaul on 2006-03-12
I've temporarily solved the problem by disabling DPMS.

---

