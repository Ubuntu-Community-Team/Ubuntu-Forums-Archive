---
title: "Something wrong happened during a package installation."
date: 2010-12-29
forum: General Help
---

### Post by colobix on 2010-12-29
Hey. During an installation of a deb package ubuntu freezed.
Now I can't install anything, and it says I have to reinstall that package but it can not find it (or something).
How can I fix this?

---

### Post by colobix on 2010-12-29
I fixed it. Took a mega chance.
The thing is. I downloaded the package from another website so I was afraid that the package overwrote some important system data or something.
But lucky me it wasn't that scary.
So I took a chance and force installed it.
So here's how I solved it (just so this thread isn't just a waste).
```
sudo dpkg --force-overwrite -i packagename.deb
```

---

