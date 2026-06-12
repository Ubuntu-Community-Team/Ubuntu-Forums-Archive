---
title: "relocation error after lucid upgrade"
date: 2010-08-05
forum: General Help
---

### Post by tsphere on 2010-08-05
Hi,

I use a software called Affymetrix Power Tools (biology stuff), and since upgrading to lucid I can't get it to run:
> 
apt-probeset-genotype: relocation error: /lib/libnss_files.so.2: symbol __rawmemchr, version GLIBC_2.2.5 not defined in file libc.so.6 with link time reference


Browsing around, it appears people have been getting this error in lucid with Folding @ Home as well, it appears to be a problem with the glibc package.
The problem is I couldn't find a fix anywhere.

Any help would be appreciated!

Thanks,

Eyal

---

