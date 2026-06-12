---
title: "delete all files with certain characters?"
date: 2010-11-11
forum: General Help
---

### Post by owners4life5 on 2010-11-11
how do i delete any single one of the files in my whole disk that say something along the lines to "chromium os"?? 

i.m just wondering because i tried to install through virtual box and failed, and probably have three different partitions consisting of nothing.

if a different method can be suggested, please do

thanks,

---

### Post by owners4life5 on 2010-11-13
bump

---

### Post by nothingspecial on 2010-11-13
Be very careful, Do this first
```

find / -type f -name 'chromium os'
```

If you definitely want to delete all those files, then do this -


```
find / -type f -name 'chromium os' -exec rm '{}' \;
```

---

### Post by owners4life5 on 2010-11-14
thank you (: worked like a charm..

marking as solved.

---

