---
title: "Package manager won't allow any new installations"
date: 2010-07-20
forum: General Help
---

### Post by seers on 2010-07-20
...even those "provided by Ubuntu." Instead, I receive an error window that says the source is untrusted. Details reveal only the name of the package I am trying to install.

I am using Lucid Lynx on an IBM ThinkPad X41.

---

### Post by J V on 2010-07-20
Try these commands:
```
sudo apt-get update
sudo dpkg-reconfigure -a
```

---

### Post by seers on 2010-07-20
That solved the problem, thanks!

---

