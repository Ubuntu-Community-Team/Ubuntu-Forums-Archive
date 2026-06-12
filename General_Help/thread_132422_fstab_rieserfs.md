---
title: "fstab rieserfs"
date: 2006-02-18
forum: General Help
---

### Post by antdengineer on 2006-02-18
Hey,

How does one mount rieserfs in fstab so that others besides root can write to it?    I usually add umask=??? to my vfat partitions but mount gives an error when I try that

---

### Post by cronholio on 2006-02-18
That's what I do and it works:

```
/dev/hda1       /               reiserfs notail          0       1
```

---

