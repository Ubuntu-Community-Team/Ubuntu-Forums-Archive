---
title: "Hide files for certain users?"
date: 2009-12-29
forum: General Help
---

### Post by shade5 on 2009-12-29
Hi,

```
.file
```

hides the file for all. But I want to hide it for certain users. Also it should be really hidden and not pseudo hidden.

Thanks.

---

### Post by Some Penguin on 2009-12-29
Put it in a directory where only the owner and members of a specific group have permissions.   You're not going to get more fine-grained control because there's no real access control list format, assuming that you're really after preventing people from seeing that something exists and not just stopping them from reading or writing it.

---

