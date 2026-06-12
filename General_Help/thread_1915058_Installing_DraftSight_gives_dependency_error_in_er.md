---
title: "Installing DraftSight gives dependency error in error"
date: 2012-01-25
forum: General Help
---

### Post by vancouverite on 2012-01-25
Hello,
I'm trying to install DraftSight but keep getting a dependency error, however, my version of the library meets the install criteria:

```
$ sudo dpkg -i --force-architecture DraftSight.deb
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 **pre-depends on libexpat1 (>= 2.0.1-4)**
dpkg: error processing DraftSight.deb (--install):
 pre-dependency problem - not installing dassault-systemes-draftsight:i386
Errors were encountered while processing:
 DraftSight.deb
```

When I check the version of libexpat1, it is indeed > 2.0.1-4:

```
$ dpkg -s libexpat1
Package: libexpat1
Status: install ok installed
Multi-Arch: same
Priority: optional
Section: libs
Installed-Size: 404
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: expat
**Version: 2.0.1-7ubuntu3**
Depends: libc6 (>= 2.4)
Pre-Depends: multiarch-support
Conflicts: wink (<= 1.5.1060-4)
Description: XML parsing C library - runtime library
 This package contains the runtime, shared library of expat, the C
 library for parsing XML. Expat is a stream-oriented parser in
 which an application registers handlers for things the parser
 might find in the XML document (like start tags).
Homepage: http://expat.sourceforge.net
Original-Maintainer: Debian XML/SGML Group <debian-xml-sgml-pkgs@lists.alioth.debian.org>
```

How can I resolve this?  Can I force dpkg to use the version I have?  Can I modify the .deb control file?  If I do that, how do I re-package it again?

Thanks for all your help.

---

