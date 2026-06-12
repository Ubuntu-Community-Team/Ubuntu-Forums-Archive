---
title: "64 bit check"
date: 2009-08-09
forum: General Help
---

### Post by kentcb on 2009-08-09
OK, time for a stupid question. How do I check whether my current installation is 64 bit or 32?

Thanks

---

### Post by howefield on 2009-08-09
Open a terminal and type

```
uname -a
```

If it has x86_64 anywhere in the output, you are running 64 bit. Otherwise it is 32 bit.

---

