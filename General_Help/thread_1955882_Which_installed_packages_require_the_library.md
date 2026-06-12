---
title: "Which installed packages require the library"
date: 2012-04-10
forum: General Help
---

### Post by t1497f35 on 2012-04-10
Hi,
Is there a command to detect what installed packages (programs) on my computer depend/use a given installed library, say "libgegl-0.0-0"?

---

### Post by haqking on 2012-04-10
> **t1497f35 said:**
> Hi,
Is there a command to detect what installed packages (programs) on my computer depend/use a given installed library, say "libgegl-0.0-0"?

```
ldd --option <pathtoapp>
```

```
man ldd
```

---

