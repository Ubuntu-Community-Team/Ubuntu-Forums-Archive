---
title: "ignore particular volumes"
date: 2011-04-21
forum: General Help
---

### Post by jettjunker on 2011-04-21
I have a PCI express raid setup of SSDs for windows, and I want Ubuntu to leave it alone completely.  I want to set ubuntu to ignore it as early as possible in the boot process, preferably without accessing it at all (let alone listing it in Nautilus' computer:///, and open/save dialogs, etc).  If Ubuntu has to access it briefly just for the uuid, label, or whatever else and compare it against a blacklist of some kind in order to ignore it thenceforth, that would be fine.

Anyone know how to do this?  The partitions are /dev/dm-1 and /dev/dm-2, and the drives are /dev/sdc and /dev/sdd.

---

