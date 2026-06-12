---
title: "Ubuntu tries to mount non-existing partition/drives"
date: 2011-07-05
forum: General Help
---

### Post by aoniumo on 2011-07-05
Here's another problem for me.  Yesterday, I deleted/reformatted one of my internal hard drive which had two partitions.  Now everytime I log-in, Ubuntu tries to mount the two partitions that no longer exist.  The only way I can resolve this is by pressing "S" twice while trying to log in to skip the auto-mounting process.  Is this problem in the grub or should I just disable auto-mounting?

Auto-mounting was enabled automatically when I installed ubuntu in May, so I have no idea how to disable it or how to mount drives that are not automatically mounted at log in.

---

### Post by seawolf167 on 2011-07-05
You need to delete the entries that point to drives/partitions which no longer exist from /etc/fstab

```
sudo cp /etc/fstab /etc/fstab.bak
gksu gedit /etc/fstab
```

then delete the bad entries, save and exit.

---

### Post by aoniumo on 2011-07-05
Ok. That worked

---

### Post by aoniumo on 2011-07-05
Ok. That worked

---

### Post by seawolf167 on 2011-07-05
> **aoniumo said:**
> q                                             z

??

---

