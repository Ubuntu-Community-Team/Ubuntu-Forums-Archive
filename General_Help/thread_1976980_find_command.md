---
title: "find command"
date: 2012-05-09
forum: General Help
---

### Post by adit on 2012-05-09
The following command
```
find ~
```
prints all files in home directory recursively.
In the above output I want to exclude Music directory (and their subdirectories recursively).  How to do that?

---

### Post by steeldriver on 2012-05-09
you should be able to use the -prune option, e.g.

```
find ~ -name Music -prune -o -print
```

---

### Post by Vaphell on 2012-05-09
and if you need only files, then add *-type f* after *-o*

---

