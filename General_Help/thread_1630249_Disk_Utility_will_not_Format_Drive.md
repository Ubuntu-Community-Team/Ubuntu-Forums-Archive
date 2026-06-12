---
title: "Disk Utility will not Format Drive"
date: 2010-11-24
forum: General Help
---

### Post by vsh3r on 2010-11-24
Hi,

Right clicking on a drive will format the drive but Disk Utility 2.30.1 included with Ubuntu 10.10 will not format the drive and says the drive is busy.

(SEE ATTACHED SCREEN-SHOT)

V$H.

:o

---

### Post by lmarmisa on 2010-11-24
Maybe the partition is mounted.

```

mount

```

Other alternative is to use GParted:

```

sudo apt-get install gparted

```

Then System -> Administration -> Gparted.

This tool shows a keyring icon on those partitions that are mounted. Even you will be able to unmount them using the right button of the mouse.

---

### Post by ezsit on 2010-11-24
Your screenshot shows that the drive is mounted. Unmount the drive and it should work.

---

