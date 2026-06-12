---
title: "looping grep"
date: 2010-05-29
forum: General Help
---

### Post by Cowboybebop79 on 2010-05-29
Ok so I have program writers block and I could do with a point int he right direction I have a task to grep for around 370 different strings which are listed in a separate file the strings are one per line eg.

```

A
B
C
D

```

and I have a stack of files that need to be grep'd 1.txt 2.txt 3.txt etc.
each of the files needs to be checked for A B C D what I need is a way to combine a for line do loop with a grep command including a variable relating to the line that the loop has got to so far.

any help would be appreciated.

---

### Post by sisco311 on 2010-05-29
```
grep -f path/to/file *.txt
```

---

