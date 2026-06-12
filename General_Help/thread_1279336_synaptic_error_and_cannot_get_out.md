---
title: "synaptic error and cannot get out"
date: 2009-09-30
forum: General Help
---

### Post by texas.chef94 on 2009-09-30
I was downloading from synaptic and by mistake choose freevo, then tried to halt it or get out and got myself into a fix I cannot get out of. When I click on synaptic pkg. mgr. this error msg displays. Please advise on course to follow to resolve this. Thank yoy

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by oldos2er on 2009-09-30
Open a terminal and run
```
sudo dpkg --configure -a
```

---

### Post by texas.chef94 on 2009-09-30
> **oldos2er said:**
> Open a terminal and run
```
sudo dpkg --configure -a
```

Worked like a charm and this old man in Texas thanks you

---

