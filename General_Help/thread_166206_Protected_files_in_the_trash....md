---
title: "Protected files in the trash... ???"
date: 2006-04-26
forum: General Help
---

### Post by Zorro on 2006-04-26
Anyone know of a way to empty the trash with protected files in there :/

It wont let me delete them, (i have no idea how they got into there).. :(  

Any help would be appreciated.. Thanks..

---

### Post by professor_chaos on 2006-04-26
assuming its your trashcan...

try "sudo rm -i ~/.Trash/*"

---

### Post by Qrk on 2006-04-26
Run nautilus as root, its the easiest way.

```
gksudo nautilus
```

Your trash folder is /home/yourusrname/.Trash (not root's .Trash in the root directory)

---

