---
title: "syntax error in VERSION script"
date: 2010-02-16
forum: General Help
---

### Post by shariefbe on 2010-02-16
when cross compiling libpng i get this error. I googled for it but i didnt get exact answer. Anybody knows what will be the problem?
```

/mnt/freescale/toolchain/bin/../lib/gcc/arm-none-linux-gnueabi/4.4.1/../../../../arm-none-linux-gnueabi/bin/ld:libpng.vers:2: syntax error in VERSION script
collect2: ld returned 1 exit status

```
i have these content inside "libpng.vers"
```

PNG12_0 {global:
local: *; };

```

---

