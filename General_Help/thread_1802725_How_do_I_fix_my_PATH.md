---
title: "How do I fix my PATH?"
date: 2011-07-12
forum: General Help
---

### Post by alarinn on 2011-07-12
I installed the full suite of packages to get ruby and rails up and running via rvm.  The issue is once I installed NetBeans I can't get to any of the packages like ruby -v.  I can see the ruby folder, so I'm thinking installing netbeans wiped out my paths to ruby, rails, gem, etc.  RVM still works and so does mysql.  Any ideas?

---

### Post by seawolf167 on 2011-07-12
Two things

1. what is the output of

```
echo $PATH
```2. where is ruby installed

```
locate *name*
```

---

