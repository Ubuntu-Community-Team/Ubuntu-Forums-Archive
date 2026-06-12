---
title: "Can I hard disk check from command line?"
date: 2011-11-24
forum: General Help
---

### Post by OsakaWilson on 2011-11-24
Is it possible to do a check of the hard disk from the command line?

---

### Post by Script Warlock on 2011-11-24
check disk space? > df -h

---

### Post by oldos2er on 2011-11-24
> **OsakaWilson said:**
> Is it possible to do a check of the hard disk from the command line?

Do you mean fsck? ```
sudo touch /forcefsck
``` will cause fsck to be run on the next boot.

---

