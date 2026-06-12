---
title: "cat /proc/meminfo"
date: 2006-01-20
forum: General Help
---

### Post by halfvolle melk on 2006-01-20
Hi,

Is there a way to break down 'meminfo' into the seperate SIMMs/DIMMs that make up the total memory? They don't always say what they pack from the outside. I also came across this nifty stuff 'cat /proc/cpuinfo' and 'df'. What more tools are there to disect your systems hardware?

Cheers,
Halfvolle melk

---

### Post by darth_vector on 2006-01-20
lspci gives you information about your pci devices
ddcprobe gives you information about your display
free gives info on system memory usage
alsamixer lets you fix up your sound preferences

and there is heaps of info in the /proc filesystem

---

### Post by az on 2006-01-20
Using lm-sensors, you can see each chip's eeprom individually.

---

### Post by halfvolle melk on 2006-01-21
Great, thank you both!

---

