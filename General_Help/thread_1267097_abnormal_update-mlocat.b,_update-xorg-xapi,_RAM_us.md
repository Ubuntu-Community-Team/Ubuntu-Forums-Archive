---
title: "abnormal update-mlocat.b, update-xorg-xapi, RAM usage"
date: 2009-09-15
forum: General Help
---

### Post by esalnoj on 2009-09-15
Whenever I'm online via ethernet,once daily, I see a large block of system and nice on the proc monitor, followed by a section of I/O wait and user on the proc monitor.

Running top during these times revealed update-apt-xapi was using ~98% CPU during the system/nice block.
After a 15 second pause, updateb-mlocat was using approximately 50% proc.

Also, Clearing firefox browser adds 5% of cache to RAM usage.
Also, when I play .avi, .mkv, .mp4 files with totem, my cache on RAM usage never drops off after closing totem.

Is this normal?
How do I correct this if it isn't?

Thanks in advance. I will perform any diagnostics you request.

Edit: update-mlocat.b showing up once per week.
      RAM while online =20% now.

---

### Post by esalnoj on 2009-09-15
11 hour bump.

---

### Post by esalnoj on 2009-09-21
**Solved** update-apt-xapi until previously filed bug report is fixed.

---

