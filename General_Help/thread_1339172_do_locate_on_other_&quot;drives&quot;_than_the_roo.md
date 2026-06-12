---
title: "do locate on other &quot;drives&quot; than the root"
date: 2009-11-27
forum: General Help
---

### Post by cthlhu1987 on 2009-11-27
How to do locate on other "drives" than the root?

---

### Post by dcstar on 2009-11-28
> **cthlhu1987 said:**
> How to do locate on other "drives" than the root?

There are no "drives" in Linux, only devices that can be mounted at particular mount points.

Until you mount them (and then access them via the mount point), then they are not accessible.

---

### Post by cascade9 on 2009-11-28
True dcstar.

If the drives are mounted, but you cant remember the mount points, system monitor (file system tab) tells you where they are, what file system, size and free space. 

Theres probably other GUI ways of finding that info.

---

### Post by bodhi.zazen on 2009-11-28
You can use a number of options.

```
sudo fdisk -l
```

If you want a gui, use gparted.

Other options include

parted, bklid, mount, cat /proc/mounts and probably more.

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning")

---

### Post by cthlhu1987 on 2009-11-30
I mean the "locate" commando...

---

