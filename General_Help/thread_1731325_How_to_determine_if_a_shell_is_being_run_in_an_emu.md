---
title: "How to determine if a shell is being run in an emulated or virtual terminal?"
date: 2011-04-17
forum: General Help
---

### Post by l07 on 2011-04-17
In a shell script. And use that in a condition.
Something like:
```

if(pts) echo "emulated"
if(tty) echo "virtual"

```

---

### Post by l07 on 2011-04-17
Isn't there a way?

---

### Post by TeoBigusGeekus on 2011-04-17
```
#!/bin/bash
cond=$(tty)
if [[ $cond == *pts* ]]; then
echo emulated 
elif [[ $cond == *tty* ]]; then
echo virtual 
fi
```

---

### Post by l07 on 2011-04-17
Thanks.

---

