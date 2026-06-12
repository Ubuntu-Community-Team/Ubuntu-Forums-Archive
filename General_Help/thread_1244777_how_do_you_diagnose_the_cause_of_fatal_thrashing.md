---
title: "how do you diagnose the cause of fatal thrashing?"
date: 2009-08-19
forum: General Help
---

### Post by ireneshusband on 2009-08-19
All too frequently my machine starts thrashing itself to death for no obvious reason. How do I work out what is causing this? Usually the thrashing becomes so bad so quickly that the desktop becomes unresponsive before I can do anything and I simply have to force a shutdown by holding down the power button. On rare occasions I have been able to start htop before the machine becomes completely unusable. However I see no sign of CPU hogging or of excessive memory use.

I suspect that the thrashing may be abnormally disruptive because one partition is encrypted using encfs. I did post an encfs bug report, believing that encfs itself could be the problem, but the developers are adamant that encfs could not cause this.

Any other ideas as to how to work out what is going on?

Many thanks in advance.

---

### Post by pqwoerituytrueiwoq on 2009-08-19
the long process of going through log files /var/log/

---

