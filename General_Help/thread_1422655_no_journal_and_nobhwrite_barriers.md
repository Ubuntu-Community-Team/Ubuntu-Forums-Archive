---
title: "no journal and nobh/write barriers"
date: 2010-03-05
forum: General Help
---

### Post by Intrepid Ibex on 2010-03-05
Do I need to manually set barrier=0 in fstab, if I have no journal in ext4?

---

### Post by Intrepid Ibex on 2010-03-05
Bump, not hard to answer if you just know the answer (heh).

---

### Post by Intrepid Ibex on 2010-03-06
blolump

---

### Post by Intrepid Ibex on 2010-03-11
Another bump

---

### Post by Intrepid Ibex on 2010-03-12
Stupid me (and maybe others too for not realizing this) - the write barriers will have no effect on an unjournalized ext3/4 because the checksumming is only being done when writing stuff to journal. So if there is *no* journal, no checksumming can be done anyway.

As what comes to nobh, associating buffer heads can only be avoided when mounting in data=writeback mode.

---

