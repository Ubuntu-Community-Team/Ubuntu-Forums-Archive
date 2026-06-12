---
title: "HTOP too many cores"
date: 2010-08-29
forum: General Help
---

### Post by jfreak53 on 2010-08-29
So I have this VPS system running Linux, and the NOC I am using just upgraded the machine to 24 cores instead of 8.  This caused a major problem when I use HTOP, now the information I need to see is so low on my SSH screen I can't see it.  How do I limit HTOP to showing X number of cores?  So I can actually see all my info?

---

### Post by jfreak53 on 2010-08-30
Any ideas on limiting this thing?

---

### Post by demosthenese on 2010-08-30
In Htop, hit F2.

Use the cursor to select Available Meters->add CPU average, F5 to add to left column.

Use the cursor to select Left Column->all CPUs, F9 to remove.


This will give one bar for CPU average instead of separate bars for each cpu.

---

### Post by jfreak53 on 2010-08-30
Sweet, thanks!

---

