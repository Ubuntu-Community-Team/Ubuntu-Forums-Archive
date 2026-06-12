---
title: "find hidden folders and files"
date: 2010-03-29
forum: General Help
---

### Post by jbumgar on 2010-03-29
how could i find a hidden folder so that i can update a file.

---

### Post by readycarpenter on 2010-03-29
in you file browser press control+h to show hidden files

---

### Post by bigsmitty64 on 2010-03-29
been wondering about that myself. Thanks!

---

### Post by andrew.46 on 2010-03-29
Hi jbumgar,

> **jbumgar said:**
> how could i find a hidden folder so that i can update a file.

You could always use the following:

```
find $HOME -type d -name '\.*'
```

All the best,

Andrew

---

