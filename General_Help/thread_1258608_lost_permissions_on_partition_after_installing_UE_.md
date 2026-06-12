---
title: "lost permissions on partition after installing UE 2.3"
date: 2009-09-05
forum: General Help
---

### Post by chris1950 on 2009-09-05
Replaced Jaunty 9.0.4 with UE 2.3. Kept the same partitions but when installed reformated them from EXt3 to Ext4. Partitions are swap, /, /home, /data   all on the same HD. I can not access /home or /data to make folders (permission denied). I tried using chmod to change permissions  also denied???? :confused:

---

### Post by Liolikas on 2009-09-05
**sudo chown** *name*
first

---

### Post by chris1950 on 2009-09-05
> **Liolikas said:**
> **sudo chown** *name*
first

Thanks worked like a charm:D

---

