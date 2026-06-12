---
title: "Problems with open office and lucid"
date: 2011-06-03
forum: General Help
---

### Post by Rgibbons on 2011-06-03
I am having problems opening and printing word 97/2000 formatted documents that were saved using OpenOffice in Maverick. If I try to open one of these files in openOffice for Lucid, it causes OpenOffice to freeze every time. 

If I save the files in OpenOffice format and share them between Maverick and Lucid - everything works fine.


Anyone know what might be causing OpenOffice in Lucid to freeze when loading word 97/2000 files?

---

### Post by Rgibbons on 2011-06-05
With further investigate, the problem appears to be the save as/open in MS word 97/2000. Opening or saving as in OpenOffice causes it to freeze.

---

### Post by AlphaLexman on 2011-06-05
Start OpenOffice from a terminal and post any errors.
```
oowriter documentname.odt
```

---

### Post by Rgibbons on 2011-06-05
What I thought was freezing actually turned out to be an exceedingly long time. If I wait long enough it will unfreeze. Opening or saving in MS word format takes two to three minutes. These are just simple one page of text files. I have .6 gig of RAM installed. Could this be a memory issue?

---

### Post by AlphaLexman on 2011-06-05
Just a guess here but, I think it might have to do with the revisions of the original document. Try opening the file in Read-Only mode:
```
oowriter -view documentname.odt
```
How long did it take?

---

### Post by Rgibbons on 2011-06-05
same result. Thanks for the suggestion.

---

