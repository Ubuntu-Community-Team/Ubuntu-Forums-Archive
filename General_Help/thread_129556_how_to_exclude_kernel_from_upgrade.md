---
title: "how to exclude kernel from upgrade?"
date: 2006-02-14
forum: General Help
---

### Post by shams2 on 2006-02-14
hi,
how to exclude kernel from apt-get upgrade?

---

### Post by ivanhelguera on 2006-02-14
Synaptics could be a solution: 
you update, mark all upgrades, and then you deselect the kernel.
I am pretty sure that there are nicer way to achieve this, editing the apt-get config file.
IH

---

### Post by dcstar on 2006-02-14
[QUOTE=shams2]hi,
how to exclude kernel from apt-get upgrade?[/QUOTE]
Select it in Synaptic, and then Package-Lock Version.

---

