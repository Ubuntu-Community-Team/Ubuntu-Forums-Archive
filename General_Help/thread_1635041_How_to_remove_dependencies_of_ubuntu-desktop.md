---
title: "How to remove dependencies of ubuntu-desktop"
date: 2010-12-01
forum: General Help
---

### Post by mr_Loki on 2010-12-01
I installed xubuntu-desktop and want to remove gnome and it`s stuff. How can I do it without typeing of all packages in sudo apt-get remove?

---

### Post by TeoBigusGeekus on 2010-12-01
```
sudo apt-get purge gnome-desktop;sudo apt-get autoremove
```

---

