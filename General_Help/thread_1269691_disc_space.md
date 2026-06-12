---
title: "disc space"
date: 2009-09-18
forum: General Help
---

### Post by pappy09 on 2009-09-18
I recently added a new hard drive to my computer so I could start using ubuntu, When I  went to install updates from update manager, it told me I need 415 m of disc space in order to install the updates. why doesn't ubuntu recognize my new hard drive, I now have lots of free space.:(

---

### Post by Liolikas on 2009-09-18
Ubuntu keeps all important stuff in / partition.
So you have to mount your new drive to start using it.
Grab software like **gparted** to prepare things.
If you still feel you need more advice post output of:
```

sudo fdisk -l

```

---

### Post by ajgreeny on 2009-09-18
How big is your first disk and how much spare room does that have?  Show us the output of both the **fdisk** command asked for by liolikas and also the output of ```
df -h
```with both disks mounted.

---

