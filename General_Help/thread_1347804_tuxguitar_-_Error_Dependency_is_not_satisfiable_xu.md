---
title: "tuxguitar - Error: Dependency is not satisfiable: xulrunner-1.9"
date: 2009-12-06
forum: General Help
---

### Post by Screatch on 2009-12-06
Whenever i try to install tuxguitar, i get error Error: Dependency is not satisfiable: xulrunner-1.9.

Any solutions?

---

### Post by mc4man on 2009-12-06
Try searching tuxguitar in synaptic and install from there.
There could be a couple of reasons why xulrunner-1.9.1 won't install

You have a conflicting package installed (synaptic will deal with that
or
you don't have all the ubuntu sources enabled
System -> Admin. -> Software Sources - first 4 on main page, first 2 under the 'Updates' tab

running this won't hurt (if all relevant sources are enabled
```
sudo apt-get update
```

---

### Post by Screatch on 2009-12-06
It was my bad and i didn't pay attention that tuxguitar is already in repositories.
Thanks.

---

