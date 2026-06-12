---
title: "xpdf - segmentation faults"
date: 2011-07-03
forum: General Help
---

### Post by George Heine on 2011-07-03
Helllo, just installed Ubuntu 11.04 on a Toshiba NB505.   Ran apt-get to install xpdf, dpkg -l gives me 
```
ii  xpdf           3.02-12ubuntu2 Portable Document Format (PDF) reader
```Have tried it on numerous PDF documents that never gave me a problem before (and display just fine using evince).  The result is always the same, a message like

```

***** MediaBox = ll:0,0 ur:362.835,272.126
***** CropBox = ll:0,0 ur:362.835,272.126
***** Rotate = 0
Segmentation fault[

```Tried using 
```
sudo apt-get remove xpdf
sudo apt-get install xpdf 
```No luck.
Any ideas?

thank you !!!

---

### Post by George Heine on 2011-07-05
Turns out that this is a known bug in Natty.  For details (and a workaround), see
[https://bugs.launchpad.net/ubuntu/+source/xpdf/+bug/669211](https://bugs.launchpad.net/ubuntu/+source/xpdf/+bug/669211)

  Will mark this thread as "solved" once a fix makes it into the regular Ubuntu repository.

---

