---
title: "detecting  undamaged/corrupt PDF"
date: 2009-10-30
forum: General Help
---

### Post by jonathonblake on 2009-10-30
All:

Can  somebody point me to a tool or script that can rapidly determine whether or not a PDF is corrupt.  I downloaded a number of PDFs, and have just discovered that a significant percentage were corrupted during the download.  

Whilst opening up each PDF, to see if it displays correctly works, it  is a  time intensive,labour intensive operation. I don't have MD5 or other  hashes for any of these files.

jonathon

---

### Post by alphaniner on 2009-10-30
This is a shot in the dark, but try to open one of your corrupt PDFs with pdfinfo:

```
pdfinfo corrupt.pdf
```

There are also a lot of other command-line pdf tools installed by default, do

```
apropos pdf
```

to get a list.

---

