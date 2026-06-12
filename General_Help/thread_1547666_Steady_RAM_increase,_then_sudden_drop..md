---
title: "Steady RAM increase, then sudden drop."
date: 2010-08-07
forum: General Help
---

### Post by alanwalterthomas on 2010-08-07
I've noticed a strange pattern with my 10.04 ubuntu x64 install with 2 GB RAM. Suppose I'm using about 1 to 1.5 GB RAM (normal). Over a timespan of several minutes RAM usage will gradually & steadily creep upwards, until for no apparent reason the system will shed ~500MB in a couple seconds, & then this process will repeat itself indefinitely.

Anybody know why this is?

---

### Post by Finalfantasykid on 2010-08-07
Souds like there could be a memory leak or something in one of the programs you are running, then is eventually freed at some point.

Do you know what process is causing this?  Check by either using 'top' or the system monitor.

---

### Post by neoargon on 2010-08-07
> **alanwalterthomas said:**
> I've noticed a strange pattern with my 10.04 ubuntu x64 install with 2 GB RAM. Suppose I'm using about 1 to 1.5 GB RAM (normal). Over a timespan of several minutes RAM usage will gradually & steadily creep upwards, until for no apparent reason the system will shed ~500MB in a couple seconds, & then this process will repeat itself indefinitely.

Anybody know why this is?

It is a bug associated with X windowing system . Nothing has to do . Some bugs in Nvidia drivers intensify the issue

---

### Post by alanwalterthomas on 2010-08-09
What's the name of the bug? Is there any chance it'll be fixed in 10.04? Something that effectively steals a quarter of my ram should qualify as major.

---

