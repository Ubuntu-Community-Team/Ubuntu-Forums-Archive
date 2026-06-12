---
title: "how change sysctl.conf file (read only)"
date: 2011-02-01
forum: General Help
---

### Post by Bit_Creepy on 2011-02-01
hi, im trying change my etc/sysctl.conf file but it won't let me as its read only. how to i change this?

---

### Post by mikewhatever on 2011-02-01
```
gksudo gedit /etc/sysctl.conf
```

All files outside your home dir are read only for regular users. This is by design.

---

### Post by Bit_Creepy on 2011-02-01
nice one, cheers mate!

---

