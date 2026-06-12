---
title: "PCI Port and PCI Bridge"
date: 2009-09-15
forum: General Help
---

### Post by Nodirbek on 2009-09-15
Hi everybody. 
I'm looking for Linux commands which gives full information about PCI Bridge type and PCI Port type. Can you help me please?! I reviewed following commands: 
sudo lshw, dmesg, lspci
but I couldn't find necessary information about PCI Port type, PCI Bridge Type, Primary Status & Health State of PCI devices.

Thanks a lot...

Regards... 
Nodir 
--------------------

---

### Post by Nodirbek on 2009-09-15
Hi everybody. 
I'm looking for Linux commands which gives full information about PCI Bridge type and PCI Port type. Can you help me please?! I reviewed following commands: 
sudo lshw, dmesg, lspci
but I couldn't find necessary information about PCI Port type, PCI Bridge Type, Primary Status & Health State of PCI devices.

Thanks a lot...

Regards... 
Nodir 
--------------------

---

### Post by ibuclaw on 2009-09-15
Please don't cross post support questions.

I've also moved this to a more relevant area, as Development tends to be more about Programming and Computer Language questions.


To answer your question though, could you perhaps review the command:
```
lspci -vvv
```
and report back whether or not that shows relevant information?

Regards
Iain

---

