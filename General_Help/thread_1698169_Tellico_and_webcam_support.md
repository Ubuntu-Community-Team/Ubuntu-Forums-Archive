---
title: "Tellico and webcam support"
date: 2011-03-01
forum: General Help
---

### Post by claudios on 2011-03-01
Does the webcam support of Tellico work?
I also try to compile from source:
-----------------------------------------------------------------------------
-- The following external packages were located on your system.
-- This installation will have the extra features provided by these packages.
-----------------------------------------------------------------------------
   * Soprano - Semantic Desktop Storing
   * Shared desktop ontologies - Desktop ontologies
   * nepomuk - Support for reading file metadata
   * taglib - Support for reading multimedia files
   * libv4l - Support for barcode scanning with a webcam

I read to issue this command and check for video or something similar
strace -e trace=open tellico

I found:
open("/dev/v4l//en_US/LC_MESSAGES/kdelibs4.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/dev/v4l//en/LC_MESSAGES/kdelibs4.mo", O_RDONLY) = -1 ENOENT (No such file or directory)

Any advice?

---

### Post by claudios on 2011-03-02
Now it works.
I installed python-gdata python-zbar python-zbarpygtk
One of these must have been useful

---

