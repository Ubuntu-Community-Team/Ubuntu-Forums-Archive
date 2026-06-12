---
title: "Database Software?"
date: 2010-02-02
forum: General Help
---

### Post by keforex on 2010-02-02
Hi,

I have been using Ubuntu for more than a year now. I have to maintain some .db files from paradox and I was wondering if anyone here know a simple solution. I can't find any easy to install and use software that can manipulate .db files. Can anyone help me? Thanks in advance!

---

### Post by jamesisin on 2010-02-02
What application was used to create the databases?

---

### Post by Zill on 2010-02-02
keforex:  OpenOffice Base supports DBase flat files...

[http://www.openoffice.org/product/base.html]("http://www.openoffice.org/product/base.html")

---

### Post by lykwydchykyn on 2010-02-02
I've had to work with Paradox in the past.  As far as native software, you can install pxlib (I think the package is called pxlib1) which gives you a utility for dumping out paradox databases into csv, sql sqlite, or HTML format so that you can look at the data or import it into another database.  I don't think any native "desktop database" applications can talk to paradox db files directly.

Having said that, Paradox installed fine in WINE last time I tried it (version 9, anyway); in fact, Corel marketed Paradox for Linux for a while (Corel even had its own Linux distro about ten years ago, which is now Xandros). I think their version was using WINE for compatibility.

---

