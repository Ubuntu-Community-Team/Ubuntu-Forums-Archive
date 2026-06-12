---
title: "what are EVMS and LVM, do I need them?"
date: 2006-05-01
forum: General Help
---

### Post by jms830 on 2006-05-01
I'm going through a howto for improving bootup speed, and I want to know: do I need EVMS (Enterprise Volume Management) or LVM? What do they do? Thanks

---

### Post by colo on 2006-05-01
EVMS and LVM2 are both technologies primarily interesting for enterprise applications, when stuff like filesystem-snapshots, data-lossless re-partitioning, on-the-fly filesystem-expansion and mirroring/striping are needed. Neither of these speeds up boot-up times (at least not on a single disk ;)), so you probably don't want to use them anyway.

---

### Post by jms830 on 2006-05-01
thanks for the reply

---

