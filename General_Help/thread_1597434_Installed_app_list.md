---
title: "Installed app list"
date: 2010-10-15
forum: General Help
---

### Post by darkcoffee on 2010-10-15
How do I view a list of installed applications in the terminal?

---

### Post by btindie on 2010-10-15
```
dpkg-query -l
```
or
```
dpkg -l
```
both do the same. Try ```
dpkg-query --help
```

---

### Post by oldos2er on 2010-10-15
Or aptitude, installed packages.

---

