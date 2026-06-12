---
title: "List of default software in 11.10?"
date: 2011-10-18
forum: General Help
---

### Post by vasa1 on 2011-10-18
I can get a list of software on my install by using```
dpkg --get-selections > installed-software
```

But is there any way to know what software is present by default on 11.10?

---

### Post by hwttdz on 2011-10-18
So a place to start is 

apt-cache depends ubuntu-desktop

which will list the dependencies of the ubuntu-desktop package, you'd need to apply some sort of cleverness to do so recursively.

---

