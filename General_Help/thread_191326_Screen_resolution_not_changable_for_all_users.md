---
title: "Screen resolution not changable for all users"
date: 2006-06-07
forum: General Help
---

### Post by jazzgossen on 2006-06-07
After installing Dapper, one of my users can no longer change the screen resolution - it's fixed at 1024x768 - although it works just fine for me.

I assume it has nothing to do with xorg.conf, since all users use the same file. Where else could those settings be stored?

---

### Post by aysiu on 2006-06-07
It's got to be somewhere in the /home/*username* folder.

See if this pops up anything... ```
grep -inr 1024 /home/*username*
```

---

