---
title: "Printing with lp produces scrambled output"
date: 2011-01-31
forum: General Help
---

### Post by SlaughterDog on 2011-01-31
So I need to print PNG files from the command line, and when I try using lp, the files print out scrambled and on several pages. Does anyone have any ideas why this can be happening? I've been googling this issue but to no avail.

It doesn't matter whether I use ```
lp -o media=Letter -o natural-scaling=100 '/var/www/rendered/1295567538.png'
``` or just ```
lp /var/www/rendered/whatever.png'
```

---

### Post by SlaughterDog on 2011-02-03
So I've realized that depending on the image's physical size (that is, not filesize or resolution but the size in inches it is intended to be printed at), it may print correctly or incorrectly.

---

