---
title: "Cannot hibernate!!!"
date: 2009-11-09
forum: General Help
---

### Post by emigrant on 2009-11-09
hi all,
if i hibernate i get an errror message "no enough swap space" and the system becomes locked (screen).
how  to enable hibernating?

thank you very much for your time.

---

### Post by konqueror7 on 2009-11-09
it means your swap space is not enough to store the current session for hibernate. the swap space is like a virtual memory (in windows). it is suggested that it be double the size of your RAM. 

also, can you print the output of the command,
```
free -m
```

---

