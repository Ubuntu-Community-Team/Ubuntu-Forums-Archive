---
title: "Vim: substitute from line x to end of file"
date: 2009-12-03
forum: General Help
---

### Post by geo909 on 2009-12-03
Hi all,

I was wondering, how can I substitute a pattern from line x to the end of file? What I am actually looking for, is the regular expression for 'end of file'.. I tried 
```

:30,\%$s/pattern1/pattern2/gc

```
but it wouldn't work..

Thanks a lot in advance..

---

### Post by DaithiF on 2009-12-04
```
:30,$s/search/replace/gc
```

---

### Post by geo909 on 2009-12-04
Thanks a lot!

---

