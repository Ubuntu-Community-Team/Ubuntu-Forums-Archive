---
title: "Recovering encrypted LVM..."
date: 2010-02-02
forum: General Help
---

### Post by jmjohn on 2010-02-02
While checking out Ubuntu Studio's installer, I somehow managed to make changes permanent and overwrite my encrypted root partition.  Though in truth I was VERY careful not to do this.

Is there any way I can recover that partition?

It reads as a single, unallocated volume now.  
```
# pvscan
  PV /dev/sda6                      lvm2 [82.66 GiB]
  Total: 1 [82.66 GiB] / in use: 0 [0   ] / in no VG: 1 [82.66 GiB]
```

Did I overwrite the lvm equivalent of a partition table, and is it even possible to restore it?

Any ideas, folks?

---

