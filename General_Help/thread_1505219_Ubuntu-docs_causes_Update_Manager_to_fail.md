---
title: "Ubuntu-docs causes Update Manager to fail"
date: 2010-06-08
forum: General Help
---

### Post by Uthene254 on 2010-06-08
Ever since I upgraded to 10.04 from 9.10, I have had the following error when Update Manager tries to run:

> Unpacking replacement ubuntu-docs ...
dpkg: ../../src/archives.c:763: tarobject: Assertion 'r == stab.st_size" failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly
A package failed to install.  Trying to recover:

When I try to uninstall ubuntu-docs, I get the following:

> installArchives() failed: dpkg: error processing ubuntu-docs (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 ubuntu-docs

When I try to reinstall it, I get:

> Unpacking replacement ubuntu-docs ...
dpkg: ../../src/archives.c:763: tarobject: Assertion `r == stab.st_size' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly

Any suggestions?

---

