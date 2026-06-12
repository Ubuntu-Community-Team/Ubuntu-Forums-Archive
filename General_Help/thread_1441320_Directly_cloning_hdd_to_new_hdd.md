---
title: "Directly cloning hdd to new hdd"
date: 2010-03-28
forum: General Help
---

### Post by pjani on 2010-03-28
I was wondering how can i clone old hdd to new hdd directly.

Is this right procedure?
sda is new hdd
sdb is old hdd
```

sudo sfdisk /dev/sda < sudo sfdisk -d /dev/sdb

```
cloning ntfs partitions.(X are ntfs partitions)
```

sudo ntfsclone --overwrite /dev/sdaX /dev/sdbX

```
cloning other partitions.
```

sudo dd if=/dev/sdbX of=/dev/sdaX bs=8MB

```

---

### Post by bobcollard on 2010-03-28
> **pjani said:**
> I was wondering how can i clone old hdd to new hdd directly.

Is this right procedure?
sda is new hdd
sdb is old hdd
```

sudo sfdisk /dev/sda < sudo sfdisk -d /dev/sdb

```cloning ntfs partitions.(X are ntfs partitions)
```

sudo ntfsclone --overwrite /dev/sdaX /dev/sdbX

```cloning other partitions.
```

sudo dd if=/dev/sdbX of=/dev/sdaX bs=8MB

```
Might try this instead:
[http://www.clonezilla.org/](http://www.clonezilla.org/)

---

