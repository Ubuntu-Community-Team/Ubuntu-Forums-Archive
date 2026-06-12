---
title: "How to rollback last update?"
date: 2010-09-24
forum: General Help
---

### Post by rva1945 on 2010-09-24
9.10

All my connection problems started after last update. 

Thanks

---

### Post by andrewthomas on 2010-09-24
look in  dpkg.log to find out what packages were updated and downgrade them.

---

### Post by rva1945 on 2010-09-24
> **andrewthomas said:**
> look in  dpkg.log to find out what packages were updated and downgrade them.

And where do I find that file?

---

### Post by andrewthomas on 2010-09-25
```
cat /var/log/dpkg.log
```

---

