---
title: "Specify which partitions auto-mount?"
date: 2010-01-08
forum: General Help
---

### Post by Cam42 on 2010-01-08
Is there any way to specify what partitions of my USB Hard drive automount? There's really only one I want mounted automatically, and I've made three partitions. I'd like it so the one mounts, but the other 2 don't. Possible?

---

### Post by Cam42 on 2010-01-09
bumpity bump.

---

### Post by Jackzor on 2010-01-09
Try 

```
sudo apt-get install ntfs-config
```

That program may work

---

### Post by rbc on 2010-01-09
Yes. It is possible by adding an entry to the /etc/fstab file. The exact wording is going to depend on some things. Open terminal, and issue these commands, then post back with the results:

sudo fdisk -l
sudo kate /etc/fstab (based on your avatar, I'm assuming your using kubuntu. If that's incorrect, issue this:
gksu gedit /etc/fstab

---

### Post by Cam42 on 2010-01-09
Yeah, KDE is too slow on the system I'm using. Will try that soon.

---

### Post by Cam42 on 2010-01-09
Yeah, KDE is too slow on the system I'm using. Will try that soon.

---

### Post by dcstar on 2010-01-10
> **Cam42 said:**
> Is there any way to specify what partitions of my USB Hard drive automount? There's really only one I want mounted automatically, and I've made three partitions. I'd like it so the one mounts, but the other 2 don't. Possible?

You use the **noauto** option in the /etc/fstab line.

---

