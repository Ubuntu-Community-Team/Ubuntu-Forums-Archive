---
title: "Is There A Way To Disable APT Authentication?"
date: 2009-06-27
forum: General Help
---

### Post by jlacroix on 2009-06-27
Hello, I generally use a lot of repositories that don't contain GPG keys. For example, KDE 4.3 Beta 2 is one of them and there are many others. Every time I update via the command line it complains about the fact that they are not authenticated packages and wants me to approve them. Is there a way to turn this off? I don't anticipate that I will ever be in a situation where I am not using a bunch of testing repo's. If anyone knows a way to fix this I will appreciate it. :)

---

### Post by synapsys on 2009-06-27
You can add the -y switch when installing. 

```
sudo apt-get install pkgname -y
```

This will tell apt to answer yes to any questions it asks. Should work.

---

### Post by jlacroix on 2009-06-27
> **synapsys said:**
> You can add the -y switch when installing. 

```
sudo apt-get install pkgname -y
```

This will tell apt to answer yes to any questions it asks. Should work.

Thank you.

That will probably work, but is there a way to completely kill it without needing a flag?

---

