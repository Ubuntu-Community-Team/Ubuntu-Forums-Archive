---
title: "VIM - vsplit when started"
date: 2010-05-14
forum: General Help
---

### Post by kekc_leader on 2010-05-14
How to run vim with two files shown with VSPLIT (using console)?

I mean, I can open 1 file: "vim a.c", then inside vim write: ":vsplit b.c", but how to do it initially from console? :)

---

### Post by gmargo on 2010-05-14
```

vim -O a.c b.c

```That's an upper-case (-O) option to split vertically.  A lower-case (-o) option will split horizontally.

---

### Post by kekc_leader on 2010-05-15
Thank you, that worked.

---

