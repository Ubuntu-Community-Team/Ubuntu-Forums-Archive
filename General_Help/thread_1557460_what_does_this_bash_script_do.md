---
title: "what does this bash script do"
date: 2010-08-20
forum: General Help
---

### Post by lorenzo.lewisjr on 2010-08-20
ls -R | grep ":$" | sed -e 's/:$//' -e 's/[^-][^\/]*\//--/g' -e 's/^/ /' -e 's/-/|/'

---

### Post by sisco311 on 2010-08-21
It lists the directory structure in a *tree view* format.

**ls -R** = list subdirectories recursively;
**grep ":$"** = print only the lines with a colon [noparse](:)[/noparse] at the end, in other words, print only the directories;
**sed -e 's/:$//'** = delete the colon from the end of the line (or replace it with nothing);
**sed -e 's/[^-][^\/]*\//--/g'** = if the directory is a subdirectory, replace its parent directories name with two minus signs (-);
**sed -e 's/^/ /'** = add a space at the beginning of the line; 
**sed -e 's/-/|/'** = replace the first minus sign with a vertical bar (|).

See:
```
man ls
man sed
man grep
```

---

