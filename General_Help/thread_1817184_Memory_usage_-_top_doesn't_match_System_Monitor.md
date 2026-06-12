---
title: "Memory usage - top doesn't match System Monitor"
date: 2011-08-03
forum: General Help
---

### Post by d86 on 2011-08-03
Hello,

running top shows:
Tasks: 165 total,   1 running, 164 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.5%us,  2.2%sy,  0.0%ni, 93.9%id,  0.5%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3721884k total,  3376604k used,   345280k free,   107524k buffers
Swap:  3855356k total,       40k used,  3855316k free,  2013536k cached

but System Monitor tells me that only 33.9% (1.2gb of 3.5gb) is being used. Why is the memory used difference so great?

Thank you

---

### Post by dcstar on 2011-08-03
> **d86 said:**
> Hello,

running top shows:
Tasks: 165 total,   1 running, 164 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.5%us,  2.2%sy,  0.0%ni, 93.9%id,  0.5%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3721884k total,  3376604k used,   345280k free,   107524k buffers
Swap:  3855356k total,       40k used,  3855316k free,  2013536k cached

but System Monitor tells me that only 33.9% (1.2gb of 3.5gb) is being used. Why is the memory used difference so great?

Thank you

Because you do not understand the difference between "Active Processes", "My Processes" and "All Processes" in the System Monitor.

---

### Post by d86 on 2011-08-03
i was going by the help page for system monitor and man page for top. i couldn't see anything there about how memory usage is calculated. can you clarify?

Thank you

---

### Post by Gyokuro on 2011-08-03
The same information will you get in case you issue following command:

free -m

and look at -/+ buffers/cache:

used means: all the memory consumed by application (apps,libs,kernel,...) and free: what's available to play with

HTH

---

