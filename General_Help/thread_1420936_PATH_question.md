---
title: "PATH question"
date: 2010-03-03
forum: General Help
---

### Post by Joe Ker1086 on 2010-03-03
ok, i have seen a couple things that, in the instructions, they require you to "add a directory to your PATH". what exactly does that mean..and how would i do that?

---

### Post by abarilla on 2010-03-03
You want to edit ~/.bash_profile and add these lines:

```
PATH=$PATH:/new/path/here
export PATH
```

Then you'll have to log out and in again.

---

