---
title: "PKG_config and gtkapp_libs error to set path."
date: 2011-11-02
forum: General Help
---

### Post by akshay.sulakhe on 2011-11-02
Hello friends, I am trying to install a app on Ubuntu 11.10.which needs Gtkmm. I am trying/tried to install that. And i am getting some errors. I will post all possible data i have on errors and config files,kindly recommend me something.Its urgent. Thanks

./configure error while installing app:-

checking for GTKAPP... configure: error: Package requirements (gtkmm-2.4 >= 2.18.0) were not met:

No package 'gtkmm-2.4' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTKAPP_CFLAGS
and GTKAPP_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


Locating gtkmm
akshay@ubuntu:~/Downloads/ariba-0.7.1/sample/hello-spovnet-0.1.0$ locate gtkmm
/usr/lib/libgtkmm-2.4.so.1
/usr/lib/libgtkmm-2.4.so.1.1.0
/usr/lib/libgtkmm-3.0.so.1
/usr/lib/libgtkmm-3.0.so.1.1.0
/usr/share/doc/libgtkmm-2.4-1c2a
/usr/share/doc/libgtkmm-3.0-1
/usr/share/doc/libgtkmm-2.4-1c2a/AUTHORS
/usr/share/doc/libgtkmm-2.4-1c2a/NEWS.gz
/usr/share/doc/libgtkmm-2.4-1c2a/README
/usr/share/doc/libgtkmm-2.4-1c2a/changelog.Debian.gz
/usr/share/doc/libgtkmm-2.4-1c2a/copyright
/usr/share/doc/libgtkmm-3.0-1/AUTHORS
/usr/share/doc/libgtkmm-3.0-1/NEWS.gz
/usr/share/doc/libgtkmm-3.0-1/README
/usr/share/doc/libgtkmm-3.0-1/changelog.Debian.gz
/usr/share/doc/libgtkmm-3.0-1/copyright
/usr/share/gnome/help-langpack/gtkmm-tutorial
/var/lib/dpkg/info/libgtkmm-2.4-1c2a.list
/var/lib/dpkg/info/libgtkmm-2.4-1c2a.md5sums
/var/lib/dpkg/info/libgtkmm-2.4-1c2a.postinst
/var/lib/dpkg/info/libgtkmm-2.4-1c2a.postrm
/var/lib/dpkg/info/libgtkmm-2.4-1c2a.shlibs
/var/lib/dpkg/info/libgtkmm-3.0-1.list
/var/lib/dpkg/info/libgtkmm-3.0-1.md5sums
/var/lib/dpkg/info/libgtkmm-3.0-1.postinst
/var/lib/dpkg/info/libgtkmm-3.0-1.postrm
/var/lib/dpkg/info/libgtkmm-3.0-1.shlibs

This is what i gave to fix it
export PKG_CONFIG_PATH=/usr/lib/pkgconfig
sudo ldconfig

Contents of configure.ac of the app to be installed
AC_INIT([hello-spovnet], [0.1.0], [])
AM_INIT_AUTOMAKE([-Wall -Werror foreign])
AC_CONFIG_SRCDIR([source/main.cpp])
AC_CONFIG_MACRO_DIR([m4])

AC_ARG_ENABLE(debug, [  --enable-debug	Enable debug options], enable_debug=$enableval, enable_debug=no)
AM_CONDITIONAL(DEBUG, test "$enable_debug" = yes)

AC_ARG_ENABLE(doxygen, [  --enable-doxygen	Enable doxygen documentation ], enable_doxygen=$enableval, enable_doxygen=no)
AM_CONDITIONAL(DOXYGEN, test "$enable_doxygen" = yes)

AC_PROG_LIBTOOL
AC_PROG_CXX
AC_PROG_CC
AC_PROG_INSTALL

AC_LANG(C++)

PKG_CHECK_MODULES([GTKAPP], [gtkmm-2.4 >= 2.18.0])

dnl Check for doxygen and features
AX_PROG_DOXYGEN

BOOST_REQUIRE([1.39])

AX_ARIBA
AX_MCPO

AC_CONFIG_FILES([
Makefile
source/Makefile
docu/Makefile
docu/doxygen/Makefile
])

AC_OUTPUT


Still i get the same error guys.

---

