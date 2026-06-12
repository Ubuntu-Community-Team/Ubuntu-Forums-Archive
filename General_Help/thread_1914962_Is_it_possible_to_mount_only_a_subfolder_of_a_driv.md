---
title: "Is it possible to mount only a subfolder of a drive?"
date: 2012-01-25
forum: General Help
---

### Post by tanoloco on 2012-01-25
Having for example an ext3 partition with subfolders like 'foo', 'doo' .. whatever, creating a mounting point under my home like /home/me/foo is it possible to mount in it only the 'foo' folder of the above drive?

:confused:

---

### Post by tanoloco on 2012-01-25
Answering to myself:

```
mount -o bind /path-to-be-mounted /path-to-mountpoint
```

Thank you anyway!

---

