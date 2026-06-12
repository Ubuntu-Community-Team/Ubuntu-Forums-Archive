---
title: "delete columns from text file"
date: 2012-07-19
forum: General Help
---

### Post by sd@ksu on 2012-07-19
I have a text file of data in 9 columns with space as delimiter. I want to delete column 3,4 without opening it and save to another file. Also I want to do from row n to row m (say), i.e., part of the file. Is there a way to do it. "awk" is in my mind. PLease help. If i get a solution in between, i shall post it here. thanks.

---

### Post by Vaphell on 2012-07-19
```
awk 'NR<=m && NR>=n { print $1, $2, $5, $6, $7, $8, $9 }' in > out
```

---

### Post by steeldriver on 2012-07-19
yes awk should work fine - or you could look at 'cut' for the columns and 'sed' to selectively print (or delete) rows

---

### Post by sd@ksu on 2012-07-19
Awesome...thanks a lot:guitar:

---

