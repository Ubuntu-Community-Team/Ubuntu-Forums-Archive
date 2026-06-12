---
title: "how can i get wget to download files from a server,ignoring some from a text file?"
date: 2010-06-29
forum: General Help
---

### Post by chriskin on 2010-06-29
I use the ```
wget -r  -A <extension> <site>
``` command to download all files from a certain site. this time i already have some of the files already downloaded and listed in a text file via ```
ls > <text file name>
```


How can i make wget to download from the site i want but ignore the filenames listed in the text file?

---

### Post by supergrav on 2010-06-29
Try running wget -nc and files you've already downloaded won't be fetched again.

---

### Post by chriskin on 2010-06-29
> **supergrav said:**
> Try running wget -nc and files you've already downloaded won't be fetched again.



wouldn't that need the files to be in the directory that wget downloads at?

i would rather avoid moving the files every time i need it to download a new one from a site , they are many (450+) and rather big

---

