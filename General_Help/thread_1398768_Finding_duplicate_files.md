---
title: "Finding duplicate files"
date: 2010-02-04
forum: General Help
---

### Post by standingwave on 2010-02-04
I've been playing around with [FSlint]("http://www.linuxjournal.com/node/1000198") and was wondering if there was any way to could check for and warn of a duplicate file before (or immediately after) you put it on your drive. 
[]("http://www.pixelbeat.org/fslint/")

---

### Post by cariboo on 2010-02-05
This more of a help question, than a Cafe thread. Moved

---

### Post by tom.swartz07 on 2010-02-05
> **standingwave said:**
> I've been playing around with [FSlint]("http://www.linuxjournal.com/node/1000198") and was wondering if there was any way to could check for and warn of a duplicate file before (or immediately after) you put it on your drive. 
[]("http://www.pixelbeat.org/fslint/")

Hey Boss,

Try this; it will compare files by size, then by MD5SUM. Its not exactly a real-time update of duplicate files, but it will list any that exist. Youre probably better off just running with fslint- that pretty much takes care of any of your needs.

```
find -not -empty -type f -printf "%s\n" | sort -rn | uniq -d | xargs -I{} -n1 find -type f -size {}c -print0 | xargs -0 md5sum | sort | uniq -w32 --all-repeated=separate
```

---

### Post by standingwave on 2010-02-05
Thanks

---

