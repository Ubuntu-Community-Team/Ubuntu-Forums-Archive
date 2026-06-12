---
title: "Preventing pdfjam flipping every 2nd page in a booklet"
date: 2012-04-01
forum: General Help
---

### Post by Nick Payne on 2012-04-01
I'm using pdfjam to create booklets from pdf files, but one thing I haven't been able to find from the documentation is how to stop the booklet pdf from having every 2nd page flipped upside down. This is the script I have at the moment to booklet an a4 pdf onto a3 paper. This gives an output pdf with the first page upside down, the second page right way up, the third page upside down, etc. I would prefer to have all pages the same way up - it just makes it easier when using a non-duplexing printer to not have to rotate the pages that have been printed on the first side when putting them back into the paper tray to print the second side:
```
#!/bin/sh 
exec pdfjam --a3paper --nup 2x1 --landscape --suffix 'booklet' --booklet true $1
```

---

### Post by lofie on 2012-10-25
hi,

this the question is a few months old - but just in case some one else is searching for the answer...

Do a man pdfbook and you see this...

SYNOPSIS
       pdfbook  [--short-edge]  [OPTION  [OPTION]  ...]  [SRC  [PAGESPEC] [SRC
       [PAGESPEC]] ...]


The slightly non obvious option you seek is "--short-edge".

Rgds
A

---

