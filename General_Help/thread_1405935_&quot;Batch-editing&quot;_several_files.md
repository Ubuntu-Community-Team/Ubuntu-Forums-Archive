---
title: "&quot;Batch-editing&quot; several files?"
date: 2010-02-13
forum: General Help
---

### Post by bokopperud on 2010-02-13
Is there a good tool for "batch-editing" a number of files non-interactively?  Replace a string with another and add a couple of lines in several files...  

sed would've been ideal, but AFAIK, sed(1) can't work on normal files.  Is it possible to get ed(1) to execute a sed-like script on a file/number of files?  Is there perhaps a cross between sed(1) and ed(1) out there?

Call me lazy, but it just seems such a waste to have to cat(1) the file through sed(1) and to a temp-file, and then overwrite the original with the temp-file...

---

### Post by falconindy on 2010-02-13
Not sure what you mean when you say sed doesn't work on "regular files". Just last night I did something akin to:

```
sed -i -e '/^package/s/ .*\;$/newpkgname/' *.java
```

Which, in place, edited about a dozen source files. Perhaps you're not aware of the -i flag?

---

### Post by bokopperud on 2010-02-23
Nope, I wasn't.  Thanks!  :-D

---

