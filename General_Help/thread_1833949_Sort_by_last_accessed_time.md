---
title: "Sort by last accessed time"
date: 2011-08-26
forum: General Help
---

### Post by ***J*** on 2011-08-26
Is there any way to sort files by last accessed time in nautilus? If not do any other file managers support this feature?

---

### Post by AlphaLexman on 2011-08-26
I don't know of a GUI solution, but from a terminal...
```
stat --format="%x, %n" * | sort
```
Will work.

**EDIT:** And if you just need the filename only...
```
stat --format="%x, %n" * | sort | awk '{print $4}'
```

---

### Post by ***J*** on 2011-08-26
Cool thanks a lot. :D

---

