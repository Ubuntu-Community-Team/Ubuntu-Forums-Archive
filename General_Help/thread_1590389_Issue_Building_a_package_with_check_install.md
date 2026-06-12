---
title: "Issue Building a package with check install"
date: 2010-10-07
forum: General Help
---

### Post by beastrace91 on 2010-10-07
I am trying to build something with checkinstall but it is throwing this error message - ```
dpkg-deb: parse error, in file '/var/tmp/tmp.tZtdRb9biy/package/DEBIAN/control' near line 3 package 'eina': field name `System' must be followed by colon
``` make install works fine, but I would like a .deb to be built. Any ideas?

~Jeff

---

### Post by andrewthomas on 2010-10-07
look in the source at the debian/control file 
 
```
 
near line 3 package 'eina': field name `System' must be followed by colon

```
 
add the colon.

---

### Post by beastrace91 on 2010-10-07
```
Source: eina
Section: libs
Priority: optional
Maintainer: Debian Pkg-e Team <pkg-e-devel@lists.alioth.debian.org>
Uploaders: Albin Tonnerre <albin.tonnerre@gmail.com>, Jan Lübbe <jluebbe@debian.org>
Build-Depends: debhelper (>= 6), cdbs, doxygen, pkg-config, libtool, automake
Standards-Version: 3.8.3
Homepage: http://www.enlightenment.org

Package: libeina
Architecture: any
Depends: ${shlibs:Depends}, ${misc:Depends}
Provides: libeina0
Conflicts: libeina0
Description: Enlightenment Foundation Library providing optimized data types
 Eina is a multi-platform library that provides optimized data types and a few
 tools. It supports the following data types:
  o Array
  o Hash Table
  o Double-linked list
  o Red-black tree
  o Shared string
  o Access Content types
    + Accessor: can access items of a container randomly
    + Iterator: can access items of a container sequentially

Package: libeina-dev
Section: libdevel
Architecture: any
Depends: ${misc:Depends}, libeina-svn-04 (= ${binary:Version}), pkg-config
Recommends: libeina-doc
Description: Development files for libeina
 Eina is a multi-platform library that provides optimized data types and a few
 tools. It supports the following data types:
  o Array
  o Hash Table
  o Double-linked list
  o Red-black tree
  o Shared string
  o Access Content types
    + Accessor: can access items of a container randomly
    + Iterator: can access items of a container sequentially
 .
 This package contains headers and static libraries for development with
 libeina.

Package: libeina-doc
Architecture: all
Depends: ${misc:Depends}
Enhances: libeina-dev
Section: doc
Description: Documentation for use with libeina
 Eina is a multi-platform library that provides optimized data types and a few
 tools. It supports the following data types:
  o Array
  o Hash Table
  o Double-linked list
  o Red-black tree
  o Shared string
  o Access Content types
    + Accessor: can access items of a container randomly
    + Iterator: can access items of a container sequentially
 .
 This package contains documentation for libeina.


Package: libeina-dbg
Architecture: any
Section: debug
Depends: ${misc:Depends}, libeina-svn-04 (= ${binary:Version})
Priority: extra
Description: debugging symbols for use with libeina
 Eina is a multi-platform library that provides optimized data types and a few
 tools. It supports the following data types:
  o Array
  o Hash Table
  o Double-linked list
  o Red-black tree
  o Shared string
  o Access Content types
    + Accessor: can access items of a container randomly
    + Iterator: can access items of a container sequentially
 .
 This package contains unstripped shared libraries. It is provided primarily
 to provide a backtrace with names in a debugger, this makes it somewhat easier
 to interpret core dumps. The libraries are installed in /usr/lib/debug and
 are automatically used by gdb.
```

The above is the output of the control file. There is no system line in it :-/ Do I just add one?

~Jeff

---

