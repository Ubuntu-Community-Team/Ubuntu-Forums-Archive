---
title: "PC crashed, dmesg from last session?"
date: 2011-03-18
forum: General Help
---

### Post by ufuser01 on 2011-03-18
Hi,

I am writing some drivers and trying to see what happened by using dmesg; But I learnt that dmesg always has the logs of the current session and the old ones are in /var/log/dmesg.*.gz

I tried to look at the contents of the .gz files, but they aren't the ones. 

I am issuing printk in my code, and towards the end, the PC crashes. Where would I be able to find these logs if dmseg doesn't have it?

Thanks.

---

