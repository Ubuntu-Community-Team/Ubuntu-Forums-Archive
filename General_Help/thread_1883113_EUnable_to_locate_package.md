---
title: "E:Unable to locate package"
date: 2011-11-18
forum: General Help
---

### Post by alpa8le on 2011-11-18
Hi,
When i try to install Ubuntu Tweak i get this error:
'E: Unable to locate package ubuntu-tweak'

---

### Post by hwttdz on 2011-11-18
I don't believe ubuntu tweak is in the default repos, try adding the ppa:tualatrix/next repo

```
sudo apt-add-repository ppa:tualatrix/next
```

then do "apt-get update" and finally "sudo apt-get install ubuntu-tweak".  

Obligatory warning, this code is not from the official repos, so only install if you trust the author.  And using sudo gives you permissions to break your system.

---

### Post by alpa8le on 2011-11-18
Thanks that worked.

---

