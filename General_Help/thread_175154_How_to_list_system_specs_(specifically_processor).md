---
title: "How to list system specs (specifically processor)"
date: 2006-05-12
forum: General Help
---

### Post by jonnyfive on 2006-05-12
I am running the ubuntu live cd on my server. I would like to know if it is detecting my four processors. Is there a way I can get ubuntu to list the processors it sees and the make etc...

---

### Post by PhrankDaChickenGeek on 2006-05-12
Open a terminal and enter:
```

sudo cat /proc/cpuinfo

```

I don't think that it would be using all 4, because the liveCD doesn't have the right kernel to support that many. But if you install, and upgrade your kernel, you should be able to use all 4 processors.

---

### Post by dcstar on 2006-05-13
[QUOTE=jonnyfive]I am running the ubuntu live cd on my server. I would like to know if it is detecting my four processors. Is there a way I can get ubuntu to list the processors it sees and the make etc...[/QUOTE]
lshw

---

