---
title: "Command - Hardware info"
date: 2010-11-04
forum: General Help
---

### Post by X.Cyclop on 2010-11-04
How can i know about my hardware? e.g. Graphics/network/sound card...

**/proc/meminfo - cpuinfo** doesn't help me.

---

### Post by ellgor on 2010-11-04
Hi,

In the main menu look in "System Tools" an app called hardinfo will list all you need.

Regards, Ellgor.

---

### Post by Vaphell on 2010-11-04
lspci in terminal
also there is a command line tool called hwinfo (sudo apt-get install hwinfo)

---

### Post by oldos2er on 2010-11-04
```
gksu lshw-gtk
```

---

