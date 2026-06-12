---
title: "Linux General, How to exec on ls results?"
date: 2010-02-10
forum: General Help
---

### Post by legendbb on 2010-02-10
Find a file and need to do something to it, think there must be a single line solution for:

$ ls *.c
$ cat *.c

Thanks,

---

### Post by rnerwein on 2010-02-10
hi
e.g.
find . -name gc.c -exec ls -l {} \;
results in ls -l gc.c
ori
find . -name gc.c -exec ./my_shell_scrip {} \;

so many possiblities
ls *.c && exec any thing  
ciao

---

