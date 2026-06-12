---
title: "Remove lib?"
date: 2006-06-04
forum: General Help
---

### Post by the slayer on 2006-06-04
When i install a program, it usually needs some exstra libs. But how do i remove the exstra lib, if i remove the program, that needed them?

---

### Post by Qrk on 2006-06-04
Apt-get doesn't have this feature, but aptitude does. I'd recommend, if you are installing a package that you will want to delete later, to install it with aptitude. They syntax is the same.

Instead of
```
sudo apt-get install package
```

Do
```
sudo aptitude install package
```

---

