---
title: "Can't install gsfonts-x11"
date: 2006-06-07
forum: General Help
---

### Post by radiant chains on 2006-06-07
I'm having a problem displaying text in certain Flash applets, and on Breezy I was able to fix the problem by install the "gsfonts-x11" package. However, when I try to install it on Dapper, it won't find the package.

```
$ sudo apt-get install gsfonts-x11
Reading package lists... Done
Building dependency tree... Done
Package gsfonts-x11 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gsfonts-x11 has no installation candidate
```

EDIT: Found the problem. dapper main repository somehow got deleted from my sources.list

---

