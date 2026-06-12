---
title: "How can I check the status of my software raid array?"
date: 2011-05-21
forum: General Help
---

### Post by Roasted on 2011-05-21
In Zentyal, it showed me active drives, if the array was degraded, and if there was any syncing happening when the array was building. How can I check that without Zentyal? Is there a terminal command or an application I can install to tell me the same information?

---

### Post by Roasted on 2011-05-23
uppp

---

### Post by jack_hmr on 2011-05-27
Gui:
Menu - System - Administration - Disk Utility (palimpsest)

Terminal:
```
cat /proc/mdstat
```

---

