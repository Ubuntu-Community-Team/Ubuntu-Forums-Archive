---
title: "removing wine"
date: 2010-03-09
forum: General Help
---

### Post by titanic74 on 2010-03-09
any help in complete removal of wine from ver 9.04 so I can start again, seem to have screwed up & cant remember how I put it in in the first place

TIA

titanic74

---

### Post by Method X on 2010-03-09
> **titanic74 said:**
> any help in complete removal of wine from ver 9.04 so I can start again, seem to have screwed up & cant remember how I put it in in the first place

TIA

titanic74

Hello
```
sudo aptitude purge wine
```

or if you want remove just wine configuretion use

```
rm -r .wine/
``` (from your home folder)

---

