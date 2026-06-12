---
title: "Terminal command help ( DU )"
date: 2011-03-21
forum: General Help
---

### Post by spiky001 on 2011-03-21
Is there a command from terminal that will show the dir you are in and list ONLY the folders (not sub folders) size, If you were in home list Downloads,Documents Pictures etc size of each folder

---

### Post by TeoBigusGeekus on 2011-03-21
```
du -h --max-depth=1|sort -h
```

---

### Post by spiky001 on 2011-03-21
I just found du -hs * but yours shows hidden I presume thks

---

