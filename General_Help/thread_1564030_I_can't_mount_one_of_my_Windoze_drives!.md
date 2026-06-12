---
title: "I can't mount one of my Windoze drives?!?"
date: 2010-08-30
forum: General Help
---

### Post by markjs on 2010-08-30
> Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdc1 is already mounted on /
mount failed

How do I fix this?  The other one mounts fine.  They are all separate physical drives.  Another oddity is in that it lists those two drives which are SATA as PATA, but I imagine that is something to do with my BIOS settings being on compatibility settings.  Anyway, thanks in advance!

---

### Post by lmarmisa on 2010-08-30
Please, show us the output of the command:

```

sudo fdisk -l

```

---

