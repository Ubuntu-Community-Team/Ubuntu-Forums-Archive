---
title: "using dpkg-buildpackage to build qt 4.7"
date: 2010-10-13
forum: General Help
---

### Post by martinpc on 2010-10-13
Hi, 
I'm trying to build Qt using dpkg-buildpackage. Briefly, the problem I have consists in that using dpkg-buildpackage I get a linking error, that I don't get if I run configure and make directly, without the mediation of dpkg-buildpackage.
One of the issues that we have is that, using dpkg-buildpackage, the configure command is not capable of finding the .qmake.cache file, so, the environment variables set in the configure script and saved in that file are not read, which causes that the apropiate linking parameters are not used.
I guess that the problem is caused by a difference in the environment of execution of the configure command. I don't know in which way the dpkg-buildpackage is changing the environment so that it makes fail the building process.

I run 'make deb-x11' to start building process using dpkg-buildpackage:
This is the main Makefile:
-----------------------------
...
X11_DEB = gvr-qt-x11-lgpl_$(X11_VERSION)_i386.deb
...
BUILDPACKAGE_ARGS = -b
BUILDPACKAGE_ARGS += -rfakeroot
BUILDPACKAGE_ARGS += -uc
...
deb-x11 $(X11_DEB):
cd x11 && dpkg-buildpackage $(BUILDPACKAGE_ARGS)
...
-----------------------------

This is the debian rules file that contains the commands for building:

---------------------------------------------------------------------------------------
#!/usr/bin/make -f
# -*- makefile -*-
# Sample debian/rules that uses debhelper.
# This file was originally written by Joey Hess and Craig Small.
# As a special exception, when this file is copied by dh-make into a
# dh-make output file, you may use that output file without restriction.
# This special exception was added by Craig Small in version 0.37 of dh-make.

# Uncomment this to turn on verbose mode.
#export DH_VERBOSE=1


# These are used for cross-compiling and for saving the configure script
# from having to guess our platform (since we know it already)
DEB_HOST_GNU_TYPE ?= $(shell dpkg-architecture -qDEB_HOST_GNU_TYPE)
DEB_BUILD_GNU_TYPE ?= $(shell dpkg-architecture -qDEB_BUILD_GNU_TYPE)
CUR_DIR ?= $(shell pwd)

QT_VERSION=4.7.0
QT_SOURCECODE_FILE=qt-everywhere-opensource-src-$(QT_VERSION).tar.bz2
UNTARDIR=$(subst .tar.bz2,,$(QT_SOURCECODE_FILE))

# choose one of the license files (doesn't really matter which one)
export QT_LICENSE_FILE=../licenses/briank10-qt-license-4.5.2.txt

untar: untar-stamp
untar-stamp:
tar -xjf $(QT_SOURCECODE_FILE)
touch untar-stamp

patch: patch-stamp
patch-stamp: untar
dpatch --workdir $(UNTARDIR) apply-all
touch patch-stamp

config.status: patch
dh_testdir
# Add here commands to configure the package.
ifneq "$(wildcard /usr/share/misc/config.sub)" ""
cp -f /usr/share/misc/config.sub config.sub
endif
ifneq "$(wildcard /usr/share/misc/config.guess)" ""
cp -f /usr/share/misc/config.guess config.guess
endif
cd $(UNTARDIR) && ./configure -confirm-license -opensource -qvfb -prefix /usr/local/Trolltech/Qt-x11-$(QT_VERSION)-qvfb -no-qt3support -debug -exceptions -openssl


build: build-stamp

build-stamp: config.status
dh_testdir

# Add here commands to compile the package.
cd $(UNTARDIR) && $(MAKE)
#docbook-to-man debian/gvr-qt-x11.sgml > gvr-qt-x11.1
# We need to make qvfb explicitly
cd $(UNTARDIR) && cd tools/qvfb && $(MAKE)

touch $@

clean:
dh_testdir
dh_testroot
rm -f build-stamp untar-stamp patch-stamp

# Add here commands to clean up after the build process.
-cd $(UNTARDIR) && $(MAKE) distclean
rm -f config.sub config.guess config.status

dh_clean 

install: build
dh_testdir
dh_testroot
dh_clean -k 
dh_installdirs

# Add here commands to install the package into debian/gvr-qt-x11.
cd $(UNTARDIR) && $(MAKE) INSTALL_ROOT=$(CURDIR)/debian/gvr-qt-x11-lgpl install
# Now we have to install qvfb as well
cd $(UNTARDIR) && cd tools/qvfb && $(MAKE) INSTALL_ROOT=$(CURDIR)/debian/gvr-qt-x11-lgpl install


# Build architecture-independent files here.
binary-indep: build install
# We have nothing to do by default.

# Build architecture-dependent files here.
binary-arch: build install
dh_testdir
dh_testroot
dh_installchangelogs ${UNTARDIR}/changes-$(QT_VERSION)
dh_installdocs
dh_installexamples
#	dh_install
#	dh_installmenu
#	dh_installdebconf	
#	dh_installlogrotate
#	dh_installemacsen
#	dh_installpam
#	dh_installmime
#	dh_python
#	dh_installinit
#	dh_installcron
#	dh_installinfo
dh_installman
dh_link
dh_strip
dh_compress
dh_fixperms
#	dh_perl
#	dh_makeshlibs
dh_installdeb
dh_shlibdeps
dh_gencontrol
dh_md5sums
dh_builddeb

binary: binary-indep binary-arch
.PHONY: build clean binary-indep binary-arch binary install 

---------------------------------------------------------------------------------------


Regards,
Martín.

---

### Post by davidmaxwaterman on 2010-11-21
> **martinpc said:**
> Hi, 
I'm trying to build Qt using dpkg-buildpackage.

Did you find a solution?

I'm trying to do a similar thing. I have been trying using source from the git repository, but there's not even a debian directory there.

I resorted to 'apt-get source' and that at least has a debian directory (of course), and the dpkg-buildpackage is doing its thing as I write - takes quite a while (even on 8-way smp).

Do you know why there is no debian directory in the git repository and how can I get it?

---

