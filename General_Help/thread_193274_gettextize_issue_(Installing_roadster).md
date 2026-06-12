---
title: "gettextize issue (Installing roadster)"
date: 2006-06-09
forum: General Help
---

### Post by danieljay on 2006-06-09
I am trying to install [Roadster]("http://linuxadvocate.org/projects/roadster/") in my ubuntu 6.06 install. When I run the install file ./autogen.sh like the readme tells me to do to install the program. It comes up with:
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.59
checking for automake >= 1.7...
  testing automake-1.7... not found.
  testing automake-1.8... not found.
  testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.22
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... not found.
***Error***: You must have glib-gettext >= 2.2.0 installed
  to build roadster.  Download the appropriate package for
  from your distribution or get the source tarball at
    [ftp://ftp.gtk.org/pub/gtk/v2.2/glib-2.2.0.tar.gz](ftp://ftp.gtk.org/pub/gtk/v2.2/glib-2.2.0.tar.gz)

checking for intltool >= 0.30...
  testing intltoolize... found 0.35.0
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.20
checking for gnome-common >= 2.3.0...
  testing gnome-doc-common... found 2.12.0
Checking for required M4 macros...
  glib-gettext.m4 not found
Checking for forbidden M4 macros...
***Error***: some autoconf macros required to build roadster
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?

I have searched all over and cannot figure out how to solve this issue. Any ideas?

---

