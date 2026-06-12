---
title: "Stuck up in creating a deb file"
date: 2010-07-01
forum: General Help
---

### Post by python.noob on 2010-07-01
Any idea for the following error while creating a deb file with the**_ dpkg-buildpackage -rfakeroot_** command.:confused::confused::confused:
"
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp configure-stamp
# Add here commands to clean up after the build process.
/usr/bin/make clean
make[1]: Entering directory `/tmp/sample-0.1+9.04'
make[1]: *** No rule to make target `clean'.  Stop.
make[1]: Leaving directory `/tmp/sample-0.1+9.04'
make: *** [clean] Error 2
dpkg-buildpackage: failure: fakeroot debian/rules clean gave error exit status 2
"
***RULES FILE as follows:***

"
#!/usr/bin/make -f
# -*- makefile -*-
# Sample debian/rules that uses debhelper.
# This file was originally written by Joey Hess and Craig Small.
# As a special exception, when this file is copied by dh-make into a
# dh-make output file, you may use that output file without restriction.
# This special exception was added by Craig Small in version 0.37 of dh-make.

# Uncomment this to turn on verbose mode.
#export DH_VERBOSE=1





configure: configure-stamp
configure-stamp:
    dh_testdir
    # Add here commands to configure the package.

    touch configure-stamp


build: build-stamp

build-stamp: configure-stamp  
    dh_testdir

    # Add here commands to compile the package.
    $(MAKE)
    #docbook-to-man debian/sample.sgml > sample.1

    touch $@

clean: 
    dh_testdir
    dh_testroot
    rm -f build-stamp configure-stamp

    # Add here commands to clean up after the build process.
    $(MAKE) clean

    dh_clean 

install: build
    dh_testdir
    dh_testroot
    dh_prep  
    dh_installdirs

    # Add here commands to install the package into debian/sample.
    $(MAKE) DESTDIR=$(CURDIR)/debian/sample install


# Build architecture-independent files here.
binary-indep: install
# We have nothing to do by default.

# Build architecture-dependent files here.
binary-arch: install
    dh_testdir
    dh_testroot
    dh_installchangelogs 
    dh_installdocs
    dh_installexamples
#    dh_install
#    dh_installmenu
#    dh_installdebconf
#    dh_installlogrotate
#    dh_installemacsen
#    dh_installpam
#    dh_installmime
#    dh_python
#    dh_installinit
#    dh_installcron
#    dh_installinfo
    dh_installman
    dh_link
    dh_strip
    dh_compress
    dh_fixperms
#    dh_perl
#    dh_makeshlibs
    dh_installdeb
    dh_shlibdeps
    dh_gencontrol
    dh_md5sums
    dh_builddeb

binary: binary-indep binary-arch
.PHONY: build clean binary-indep binary-arch binary install configure
"

---

