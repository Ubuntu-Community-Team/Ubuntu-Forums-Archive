---
title: "remove all files ending .log in folder"
date: 2012-05-31
forum: General Help
---

### Post by JigglyWiggly_ on 2012-05-31
So crashplan keeps crashing, i went to the bin folder and there's like 1 million log files. 
Nautilus crashes opening the folder (that's so pathetic)
so I tried 
ls
and it displays all the files

however, when I do
rm *.log
 I get argument list is too long
what is this madness

---

### Post by Lars Noodén on 2012-05-31
You could try using [find](http://manpages.ubuntu.com/manpages/precise/en/man1/find.1posix.html).

```

find . -name '*.log' -exec /bin/rm "{}" \;

```

---

### Post by gnusci on 2012-05-31
rm -Rf *.log

---

### Post by steeldriver on 2012-05-31
you *might* need to pipe the find through xargs - if your version doesn't do the batching natively
```
find . -name "*.log" | xargs rm
``` or if the filenames may contain spaces, 
```
find . -name "*.log" -print0 | xargs -0 rm
```

---

### Post by JigglyWiggly_ on 2012-05-31
xargs worked nicely
;>

---

