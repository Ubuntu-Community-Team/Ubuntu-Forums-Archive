---
title: "dpkg equivalent of rpm -qlf"
date: 2009-11-03
forum: General Help
---

### Post by shammi000 on 2009-11-03
Hi All,

What is the equivalent command for rpm -qlf in dpkg.

I want to know the files installed by a package.

Regards,
Shammi

---

### Post by sisco311 on 2009-11-03
```
dpkg -L package
```

---

