---
title: "Simple-Scan 3.2.0 (Oneric) generated PDF Files"
date: 2011-10-24
forum: General Help
---

### Post by JedV on 2011-10-24
I previously used Simple Scan v2.32.0 in Ubuntu 10.10... PDF Files ranged in size from 700 kb to 1 MB per page (when using 'Photo' settings, which I presume used 300 dpi scan and good quality compression).  

Recently I updated my system to Ubuntu 11.10, and Simple Scan 3.2.0 now creates huge PDF files, using the same settings the same documents are on average 25 MB!  Selecting the 'Text' quality settings results in a low quality and very small 71 kb file.  There is no happy medium.

I suspect that something changed with respect to image compression settings used in the creation of PDF files, but I can't figure out if there are any user-defined settings in this program.

Any help would be appreciated.  I much prefer simple-scan over xsane.

---

### Post by laurolyra on 2011-10-27
I have exactly the same problem. Does anyone know how to fix it?

---

### Post by _sherpa_ on 2011-10-27
Hi,

same thing there. Seems that a bug is opened on launchpad :
[https://bugs.launchpad.net/ubuntu/+source/simple-scan/+bug/853648](https://bugs.launchpad.net/ubuntu/+source/simple-scan/+bug/853648)

---

### Post by JedV on 2011-10-29
Thanks.  I'll keep my eye on the bug report.  :)

---

### Post by JedV on 2011-11-14
A fix for this issue has been rolled into version 3.2.1 of SimpleScan in Oneric.  Yay!

---

### Post by Jacobonbuntu on 2011-11-14
if you need more detailed settings, you could use Scan2pdf?

---

