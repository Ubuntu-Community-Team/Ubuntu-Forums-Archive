---
title: "lpr question &amp; two sided printing"
date: 2010-03-29
forum: General Help
---

### Post by blur xc on 2010-03-29
I just recently learned about the wonderful little lpr command- and using man -t (bash command) to beautifully print man pages for reference- but is there a way to print both sides of the paper using a printer so equipped?

BM

---

### Post by plucky on 2010-03-30
> **blur xc said:**
> I just recently learned about the wonderful little lpr command- and using man -t (bash command) to beautifully print man pages for reference- but is there a way to print both sides of the paper using a printer so equipped?

BM

Look at **man lp** as it has 
```
 -o sides=one-sided

       -o sides=two-sided-long-edge

       -o sides=two-sided-short-edge
            Prints  on  one  or  two sides of the paper. The value "two-sided-
            long-edge" is normally used  when  printing  portrait  (unrotated)
            pages, while "two-sided-short-edge" is used for landscape pages.
``` an option to specify one or two sided printing in portrait or landscape.

Don't have a duplex printer so cannot test.


Good Luck

---

### Post by blur xc on 2010-03-30
> **plucky said:**
> Look at **man lp** as it has 
```
 -o sides=one-sided

       -o sides=two-sided-long-edge

       -o sides=two-sided-short-edge
            Prints  on  one  or  two sides of the paper. The value "two-sided-
            long-edge" is normally used  when  printing  portrait  (unrotated)
            pages, while "two-sided-short-edge" is used for landscape pages.
``` an option to specify one or two sided printing in portrait or landscape.

Don't have a duplex printer so cannot test.


Good Luck

Sweet- I read the man page for lpr but I must have skipped over that part.

Thanks!
BM

---

