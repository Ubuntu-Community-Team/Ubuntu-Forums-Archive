---
title: "Character encoding change if using SGE (Sun Grid Engine)"
date: 2012-10-04
forum: General Help
---

### Post by toontu on 2012-10-04
Hi,

I tried to find the cause of the following problem but to no avail.

I have several files that are encoded in UTF-8 and some code to process these files. The char-encoding doesn't change if the code is called directly through terminal either locally or on a remote machine.

The problem now is that if I call the code through SGE, the char-encoding of the files will be automatically changed to US-ASCII. Why?

Many thanks.

---

