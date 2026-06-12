---
title: "Bibblepro 32-bit on 64-bit Ubuntu 9.10"
date: 2009-11-29
forum: General Help
---

### Post by Richard Carlson on 2009-11-29
Can't figure out how to get it to work. I've got both a *.deb and *.rpm file. I can't get the *.deb to install. Keeps saying wrong architecture. I install ia32 (I assume it will install all of the associated files). Also I think libstdc++5 is needed but it is not in the repositories. I'd like to get this bugger to work. Any help would be appreciated. 


Rich:D

---

### Post by jokker on 2009-12-06
I have the very same issue, did you find a way out buddy ?
Can't install bibblepro on ubuntu karmic !!

---

### Post by Cheesemill on 2009-12-06
```
sudo dpkg -i --force-architecture filename.deb
```

---

