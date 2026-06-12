---
title: "ubuntu 10.04  is taking so much time for booting"
date: 2010-07-23
forum: General Help
---

### Post by molykkutti on 2010-07-23
I've installed ubuntu 10.04  in dual booting mode in a windows xp pc.
after 2-3 usage it is taking much time to for booting up ..
I found the same problem exist in a ubuntu 9.1  pc also ...
pls help me to solve this problem

---

### Post by Tylerjd on 2010-07-23
Have you installed any daemons or run-at-boot programs? If not, check your SMART status if it is a SATA drive by using Disk Utility (System>Administration>Disk Utility). If it has bad sectors etc, then it may be straining to boot the OS. As with both of them having the problem, if they are IDE (PATA) Hard drives, it may be slow. Also, if you just soft-reboot to get to Ubuntu, try cold booting by shutting down all the way. And pressing the power button to start it.

---

### Post by molykkutti on 2010-07-28
no i have't installed any daemons ...

---

### Post by VorDesigns on 2010-07-28
That's weird, the first thing I noticed was how quickly my 64bit install gets met to a login prompt.
Some of the applications are a little pokey to load but booting has been a little starling.

---

