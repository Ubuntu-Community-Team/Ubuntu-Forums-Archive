---
title: "i cant download any"
date: 2010-02-11
forum: General Help
---

### Post by freefixkorma on 2010-02-11
hi there i am trying to download from the download center i am ubuntu 9.10 and there is windows that said ---waiting for other software managers to quit -----i waited for a while and it never stops any idea what can i do is being performing this for a while i will appreciate any help please

---

### Post by pmlxuser on 2010-02-11
restart machine, launch the software manager.

else try installing using apt - see what error you get

---

### Post by freefixkorma on 2010-02-11
i am getting this window in software manager 


E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.








> **pmlxuser said:**
> restart machine, launch the software manager.

else try installing using apt - see what error you get

---

### Post by oldos2er on 2010-02-11
Open a terminal, run ```
sudo dpkg --configure -a
```

---

