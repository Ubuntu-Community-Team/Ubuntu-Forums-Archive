---
title: "Extremely slow boot time"
date: 2010-12-28
forum: General Help
---

### Post by Naegling23 on 2010-12-28
My boot time is extremely slow on ubuntu 10.10, on the order of 5 or so minutes.  I've attached my var/log/bootchart, can anyone help me figure out whats wrong here?  Thanks

---

### Post by davidmohammed on 2010-12-28
... yeh - I too find it difficult to decipher those boot charts.

The only thing that struck me as odd is the very long fsck running.

Suggest one of two things

1. sudo touch /forcefsck
this will force a recheck on the next reboot and the counter will be then reset to zero so hopefully fsck will not run on subsequent boots.

2. boot from a livecd - using gparted, click on the linux partition and run a check to see if there are any further errors needing to be resolved.

---

