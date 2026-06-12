---
title: "init levels in ubuntu"
date: 2009-08-05
forum: General Help
---

### Post by marcopalla on 2009-08-05
Hi

I've not undertood ubuntu init meaning: on red hat init 3 command means to stop X and other things setted in chkconfig --list

in ubuntu if I sudo init 3 nothing happens?!?! is only X always up or no init config. I have installed chkconfig but I see X11-common S: on on runlevels and I don't know what it means

anyone smarter than me? :(
m.

---

### Post by Glyndwr on 2009-08-05
The runleveles are not the same as in redhat.  To stop X just stop the gdm service.

---

### Post by marcopalla on 2009-08-05
....interesting....

so if I disable gdm on runlevel 3 I get same result,

by the way what meaning have runlevels in ubuntu??!!

---

