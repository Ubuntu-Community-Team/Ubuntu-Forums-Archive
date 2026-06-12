---
title: "Evince showing pdf file name on title bar"
date: 2011-08-21
forum: General Help
---

### Post by peteron on 2011-08-21
evince by default shows the embedded file title, but not the file name; this is really annoying when you open a bunch of pdf files, and want to find the one you want to read.
I took use of the pdftk utility to solve this issue by removing the file title in a batch.
to install pdftk:
```
sudo apt-get install pdftk

```

download the attached file, untar to get two files (PDFTITLE, PDFINFO), put them in the directory of the pdf files, with file extension .pdf, and run:
```
bash PDFTITLE 

```

warning: doesnot work on encrypted files

---

