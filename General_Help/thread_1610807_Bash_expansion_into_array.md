---
title: "Bash expansion into array"
date: 2010-11-01
forum: General Help
---

### Post by J V on 2010-11-01
I was looking into more advanced bash topics and I found braces for expansion. I was wondering how to do this with an array... something the likes of:
```
{a..z}
**plus**
array=( ${array[@]-} $(echo "$variable") )
```

---

### Post by J V on 2010-11-02
bump

---

