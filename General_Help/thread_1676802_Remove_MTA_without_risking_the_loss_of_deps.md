---
title: "Remove MTA without risking the loss of deps"
date: 2011-01-27
forum: General Help
---

### Post by Nobby66 on 2011-01-27
I am going to use another non-debian (source tarball only) mail system, so I need to remove postfix, can someone offer hint on how to do this safely without losing all the other programs as well?  


The following packages will be REMOVED:
  lsb lsb-core lsb-cxx lsb-desktop lsb-graphics lsb-languages lsb-multimedia lsb-printing mailx postfix


and, why oh why does it need to remove mailx?  mailx doesn't even need an MTA.

---

