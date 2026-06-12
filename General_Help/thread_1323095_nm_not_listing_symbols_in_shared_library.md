---
title: "nm not listing symbols in shared library"
date: 2009-11-11
forum: General Help
---

### Post by kanato on 2009-11-11
$ nm /usr/lib/libpng.so
nm: /usr/lib/libpng.so: no symbols

but:

$ nm /usr/lib/libpng.a

lists all the symbols I expect to see. I thought nm should work for shared libraries? If not, how can I list the exported functions in a shared library?

I also tried objdump -t with the same results.

---

