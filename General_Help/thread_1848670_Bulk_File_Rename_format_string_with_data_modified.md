---
title: "Bulk File Rename format string with data modified"
date: 2011-09-23
forum: General Help
---

### Post by johntkucz on 2011-09-23
A fairly advanced question:

I have a certain format string for almost every type of file.  I have been "manually" (using pyrenamer, which rocks!) renaming them in bulk.  I was wondering if there's a way to automatically (there has to be) set up a script so that certain files will be automatically renamed with a certain format string that uses their date-modified/date-created as part of the format string.  I am guess this would involve some kind of cli script?  I am not advanced as I'd want to be yet to write such a script but would love to learn.

---

### Post by patryk77 on 2011-09-23
Can't you simply call stat -c?

Read in terminal:
man stat

```
       %x     Time of last access

       %X     Time of last access as seconds since Epoch

       %y     Time of last modification

       %Y     Time of last modification as seconds since Epoch

       %z     Time of last change

       %Z     Time of last change as seconds since Epoch

```


```
pato@toaster:/tmp$ touch privatepart
pato@toaster:/tmp$ stat -c %y privatepart 
2011-09-23 01:11:42.389941534 -0500
pato@toaster:/tmp$ stat -c %Y privatepart 
1316758302
pato@toaster:/tmp$ 
```

Should be enough to get you started.

---

