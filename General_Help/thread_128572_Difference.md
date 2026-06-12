---
title: "Difference?"
date: 2006-02-11
forum: General Help
---

### Post by kyoushu on 2006-02-11
In the livecd of Ubuntu you cannot access any of Window's files through mnt->Hda1 or something.  Is this only on the livecd?

---

### Post by dcstar on 2006-02-11
[QUOTE=kyoushu]In the livecd of Ubuntu you cannot access any of Window's files through mnt->Hda1 or something.  Is this only on the livecd?[/QUOTE]
If it is an NTFS partition, I believe you may need an additional package that might only be installed on a proper setup.

The Live CD is really just to test basic hardware functionality and the "look and feel" of Ubuntu, not give 100% operational functionality.

---

### Post by aysiu on 2006-02-11
You need the fourth link of my signature--it works for the live CD, too... I've tried it.

---

### Post by Ocxic on 2006-02-11
```

sudo mount -t ntfs /dev/hda /mountpoint -o umask=0222

```

that will mount the ntfs partition so you can get acces to it.

---

