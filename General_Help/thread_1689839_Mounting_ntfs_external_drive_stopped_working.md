---
title: "Mounting ntfs external drive stopped working"
date: 2011-02-17
forum: General Help
---

### Post by cd-r80 on 2011-02-17
Mounting ntfs external drive stopped working after installing ntfs config tool. No it says "you are not priviledged to mount the volume" What I should do to return original config & automount?

---

### Post by seawolf167 on 2011-02-17
Can you post the output of

```
sudo fdisk -l
```

and the contents of the file

```
/etc/fstab
```

---

### Post by cd-r80 on 2011-02-19
Sorry I found that it was unclean unmounting  because of freeze or something. I fixed by booting to W7. It just happened same time when I installed ntfs-config. I installed W7 after Ubuntu & I did not have acces to "Win C" without installing ntfs-config.

---

