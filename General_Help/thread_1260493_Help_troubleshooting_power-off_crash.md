---
title: "Help troubleshooting power-off crash"
date: 2009-09-07
forum: General Help
---

### Post by schwinn on 2009-09-07
I've been experiencing some problems on my laptop. While browsing sites with videos or flash, I will sometimes get a complete system crash, where the machine powers off completely. No error, no warning... just "click" and the machine is off.

This seems to happen most often when watching trailers at various websites... but again, it's not totally consistent or repeatable. I monitor CPU temperature on the task bar, and it's staying cool enough, though when watching videos it will rise to 50C, at times. Other applications can raise the temp to this level, and not show a problem...

The machine is an HP zd7000 laptop (P4 CPU). Running Ubuntu Jaunty (9.04). Was originally 8.04, I think, and I did a dist upgrade along the way to 9.04, which is where I am now.

Browser is Shiretoko, and it's running the Flash plugin 10.0 r32.

I don't expect a quick answer to this problem, but would appreciate some help on how to troubleshoot this matter. Any help is appreciated.

---

### Post by schwinn on 2009-09-07
FYI, also just ran a memtest for the past 2.5 hours - 5 passes completed with no issues found...

---

### Post by schwinn on 2009-09-21
No one has any ideas on how to troubleshoot this type of a catastrophic problem?

---

### Post by Lekensteyn on 2009-09-21
Nope, do you have any errormessages in /var/log/ ?

---

### Post by schwinn on 2009-09-24
My GF is usually using the computer, and it will click-off when she's browsing some websites - doesn't happen all the time, but it does happen.

Based on that I'm not seeing anything significant in /var/log/messages before restarts/shutdowns. Only thing I see is "exiting on signal 15" which, as I understand it, is syslogd restarting, and is not indicitive of a problem...

Is there somewhere else I should be looking?

---

