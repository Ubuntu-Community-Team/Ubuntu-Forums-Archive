---
title: "dmstat not recognised"
date: 2012-08-30
forum: General Help
---

### Post by Royalist on 2012-08-30
I have been teying to improve performance in line with the suggestions contained in : -

[HTML]https://help.ubuntu.com/community/DiskPerformance[/HTML]

```
dmstat -d /dev/sda7
``` does not work for me.

Having read the man pages over twice, I still don't know why?

Any comments please?

---

### Post by mikechant on 2012-08-30
Looks like a typo, should be 'dstat', not 'dmstat'; also, sda7 is a partition, not an actual disk, and you need '-D' not '-d'.

Try
```
dstat -D sda
```


I'd check this myself but I'm not at my Ubuntu PC.

---

