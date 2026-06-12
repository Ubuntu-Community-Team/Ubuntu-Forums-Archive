---
title: "Dual Boot to Single Boot"
date: 2010-06-03
forum: General Help
---

### Post by sun_hill on 2010-06-03
I have a Lenovo Think Pad with Ubuntu 10.04 installed along with Windows XP.  Unfortunately, some time ago, XP stopped working.  However, at that point I had gone over to principally Ubuntu anyways, so I did nothing about it.  However, at this point I just want to get rid of my XP install and solely have Ubuntu installed.  How do I go about this?  Any help here is appreciated.

---

### Post by eriktheblu on 2010-06-03
Easy.
1.Remove your NTFS partition(s) (I prefer Gparted)
2.```
sudo update-grub
```

---

