---
title: "Windows/Linux system times"
date: 2006-04-11
forum: General Help
---

### Post by LucidTaZ on 2006-04-11
Hi,

I have quite a nasty problem and tried to look for a solution myself but I couldn't find it. The problem is: Windows XP and Ubuntu Linux keep messing up the system clock. When I boot from Windows into Linux, the clock gets set back 2 hours, and when I boot from Linux into Windows, the clock gets set forward 2 hours.

In both OSses, the time zone is set to GMT+1 (Amsterdam)

Any ideas? :o

---

### Post by Ramses de Norre on 2006-04-11
```
sudo gedit /etc/default/rcS
```
Find the line UTC=yes and change it into UTC=no.

---

### Post by LucidTaZ on 2006-04-12
It worked, thanks. :)

---

### Post by ycng76 on 2006-04-22
Does Ubuntu actually changed the BIOS clock of a machine by just editing this file?
Sorry, I can't really understand what is happening here as I'm running a dual-boot(Windows/Ubuntu) pc and have encoutered the same problem

---

### Post by PriceChild on 2006-04-22
During the set up of ubuntu, you got asked a little question about whether it was the only OS on the pc, so that it would know whether it should keep the time for you. You must've not been reading properly, so it got messed up :)

And yup, Ubuntu will change it if it thinks it needs changing.

---

