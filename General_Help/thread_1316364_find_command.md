---
title: "find command"
date: 2009-11-05
forum: General Help
---

### Post by mmaru on 2009-11-05
Is it at all possible to a find command to the background. Why is the following command does not work:

find / -name "*.doc" & 2>/dev/null


Thank you.

Maru

---

### Post by diesch on 2009-11-05
Use 
```
 find / -name "*.doc" 2>/dev/null &
```
instead.

---

