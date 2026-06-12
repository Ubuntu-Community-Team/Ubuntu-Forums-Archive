---
title: "CPU Frequency Scaling Problem"
date: 2006-03-12
forum: General Help
---

### Post by blue cube on 2006-03-12
how do you turn off frequency scaling?

---

### Post by IGNIZ on 2006-03-12
just put performance in governor

---

### Post by Sutekh on 2006-03-12
You could turn off the powernow (freq-scaling) daemon with
```
sudo /etc/init.d/powernowd stop
```
There should be a way to stop to stop it loading each time at boot aswell.

---

