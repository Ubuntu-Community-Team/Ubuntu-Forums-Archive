---
title: "Checking file integrity after power loss 9.10"
date: 2010-02-24
forum: General Help
---

### Post by osomphane on 2010-02-24
Hello,

Can anyone recommend any utilities that would check the hard drive and its contents (if they are still good) following a power outage?

---

### Post by byStanderone on 2010-02-24
...you can begin by using 'disk usage analyzer'  under applications>accessories or do a forced fsck on next bootup...sudo touch /forcefsck , do not run fsck on a mounted filesystem.

---

