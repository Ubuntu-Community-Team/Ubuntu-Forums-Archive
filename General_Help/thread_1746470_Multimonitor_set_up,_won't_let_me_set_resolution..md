---
title: "Multimonitor set up, won't let me set resolution."
date: 2011-05-01
forum: General Help
---

### Post by Chaos Punk on 2011-05-01
I have an Acer Aspire 5532 running the latest Ubuntu. I'm trying to set up dual monitors, the laptops screen and an HP 2311x connected via VGA. I installed Ubuntu and was able to set it up just fine, however when I installed the proprietary video drivers from AMD and restart, it forgot my settings and even the name of the monitor, which it detected automatically before the drivers were installed. I tried to set up my HP monitor with the correct resolution, but no mater how I do it, it says it can't because it would exceed the maximum virtual screen size, is there a way to change this or a workaround?

---

### Post by ach667 on 2011-05-01
[https://wiki.ubuntu.com/X/Config/Resolution#How%20to%20setup%20a%20dual%20monitor](https://wiki.ubuntu.com/X/Config/Resolution#How%20to%20setup%20a%20dual%20monitor)

---

### Post by Chaos Punk on 2011-05-01
> **ach667 said:**
> [https://wiki.ubuntu.com/X/Config/Resolution#How%20to%20setup%20a%20dual%20monitor]("https://wiki.ubuntu.com/X/Config/Resolution#How%20to%20setup%20a%20dual%20monitor")
I already looked at that, I couldn't find anything that could help me, but I think I may have found a different solution by using Catalyst Command Center.

EDIT: I fixed it, turns out CCC seems to take priority over Ubuntu's built in Monitor manager, it's solved.

---

