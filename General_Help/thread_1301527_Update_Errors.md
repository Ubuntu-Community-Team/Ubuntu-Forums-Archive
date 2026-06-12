---
title: "Update Errors"
date: 2009-10-26
forum: General Help
---

### Post by volaer on 2009-10-26
Anybody know how to get rid of this update error?

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


Need your help badly.... Thanks!!!

---

### Post by ibutho on 2009-10-26
Run Applications -> Accessories -> Terminal and enter
```
sudo dpkg --configure -a
```
That will hopefully resolve the problem.

---

### Post by volaer on 2009-10-26
> **ibutho said:**
> Run Applications -> Accessories -> Terminal and enter
```
sudo dpkg --configure -a
```
That will hopefully resolve the problem.

Thank you very very much... I just tried it. And it did worked.:) Thanks!!! I love Ubuntu Community.

---

