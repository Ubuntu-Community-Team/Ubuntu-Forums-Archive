---
title: "would like to contribute at launchpad but can't debuild my sourcode"
date: 2011-04-02
forum: General Help
---

### Post by d3v1150m471c on 2011-04-02
There is a program i wrote in python called SplicePY. I'd like to contribute it to launchpad so people can have it right there in their repositores. It's already on sourceforge, unfortunately there are no ppa's at sourceforge for me to distrubute my software via synaptic or apt-get. I know i'm asking a lot but I really do not get these makefiles, even after spending the last day sorting through tutorials, no matter what i do i can't find a single one to make a proper .deb with debuild from my source code nor do I have the first clue about makefiles. I get error after error, some of which i don't understand and i'm at the end of my rope with digging through awful info and making something out of nothing.

You can find a .deb and the source tar under software on my project site on my signature. If someone could please tell me how to go about creating a makefile and whatnot to `debuild` this sucker i would greatly appreciate it.

---

### Post by d3v1150m471c on 2011-04-02
getting the following errors with `debuild -us -uc' command...
```

d3v11@d3v11m4ch1n3:~/splicepy-1.0$ debuild -us -uc
 dpkg-buildpackage -rfakeroot -D -us -uc
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package splicepy
dpkg-buildpackage: source version 1.0-0
dpkg-buildpackage: source changed by d3v1150m471c <d3v1150m471c@gmail.com>
dpkg-buildpackage: host architecture i386
dpkg-checkbuilddeps: error: syntax error in debian/control at line 25: first block lacks a source field
dpkg-buildpackage: warning: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: warning: (Use -d flag to override.)
debuild: fatal error at line 1340:
dpkg-buildpackage -rfakeroot -D -us -uc failed
d3v11@d3v11m4ch1n3:~/splicepy-1.0$ debuild -us -uc
 dpkg-buildpackage -rfakeroot -D -us -uc
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package splicepy
dpkg-buildpackage: source version 1.0-0
dpkg-buildpackage: source changed by d3v1150m471c <d3v1150m471c@gmail.com>
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
dh clean
dh: No packages to build.
 dpkg-source -b splicepy-1.0
dpkg-source: warning: unknown information field 'Version' in input data in general section of control info file
dpkg-source: warning: unknown information field 'Installed-Size' in input data in general section of control info file
dpkg-source: warning: unknown information field 'Architecture' in input data in general section of control info file
dpkg-source: warning: unknown information field 'Depends' in input data in general section of control info file
dpkg-source: warning: unknown information field 'Description' in input data in general section of control info file
dpkg-source: info: using source format `1.0'
dpkg-source: info: building splicepy using existing splicepy_1.0.orig.tar.gz
dpkg-source: info: building splicepy in splicepy_1.0-0.diff.gz
dpkg-source: error: cannot represent change to splicepy-1.0/debian/tmp/usr/share/doc/splicepy/changelog.Debian.gz: binary file contents changed
dpkg-source: unrepresentable changes to source
dpkg-buildpackage: error: dpkg-source -b splicepy-1.0 gave error exit status 1
debuild: fatal error at line 1340:
dpkg-buildpackage -rfakeroot -D -us -uc failed

```i attached the file that's giving me the errors...everytime i think i'm getting somewhere ^ crap happens...ugh

---

### Post by d3v1150m471c on 2011-04-02
okay...well..., i rebuilt the package. i did create makefile and the makefile works perfectly. BUT i created the debian/rules file like so:
```

#!/usr/bin/make -f
# -*- mode: makefile; coding: utf-8 -*-

%:
    dh $@

build:
    ./splice.compile

install:
    mv splice.pyc /usr/bin/splice
    mkdir /etc/splice
    cp splice.list /etc/splice/splice.list
    cp splice.manual /etc/splice/splice.manual
    rm -f splice.pyc

uninstall:
    rm -r /etc/splice
    rm /usr/bin/splice

clean:
    rm -f splice.pyc

```

i keep getting "dpkg-buildpackage: error: fakeroot debian/rules clean gave error exit status 1"
even when i remove clean from the rules file...same error. and all of this is if i use `fakeroot`
before running the `debuild -us -uc` command. If i run debuild -us -uc without having done fakeroot first it tells me i don't have permission to do anything. IE move splice to /usr/bin/... "I think and I hope" doing fakeroot && debuild -us -uc is the solution aside from the clean error i keep getting. debhelper is supposed to make this a painless process and it's become nothing but a complete bane on my existence... Here's my output:

As fakeroot -
```

root@d3v11m4ch1n3:~/Projects/SplicePY/splicepy-1.0/debian# debuild -us -uc
This package has a Debian revision number but there does not seem to be
an appropriate original tar file or .orig directory in the parent directory;
(expected one of splicepy_1.0.orig.tar.gz, splicepy_1.0.orig.tar.bz2,
splicepy_1.0.orig.tar.lzma or splicepy-1.0.orig)
continue anyway? (y/n) y
 dpkg-buildpackage -rfakeroot -D -us -uc
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package splicepy
dpkg-buildpackage: source version 1.0-0
dpkg-buildpackage: source changed by d3v1150m471c <d3v1150m471c@gmail.com>
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
fakeroot: FAKEROOTKEY set to 1227113421
fakeroot: nested operation not yet supported
dpkg-buildpackage: error: fakeroot debian/rules clean gave error exit status 1
debuild: fatal error at line 1340:
dpkg-buildpackage -rfakeroot -D -us -uc failed

```

without fakeroot...
```

d3v11@d3v11m4ch1n3:~/Projects/SplicePY/splicepy-1.0/debian$ debuild -us -uc
This package has a Debian revision number but there does not seem to be
an appropriate original tar file or .orig directory in the parent directory;
(expected one of splicepy_1.0.orig.tar.gz, splicepy_1.0.orig.tar.bz2,
splicepy_1.0.orig.tar.lzma or splicepy-1.0.orig)
continue anyway? (y/n) y
 dpkg-buildpackage -rfakeroot -D -us -uc
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package splicepy
dpkg-buildpackage: source version 1.0-0
dpkg-buildpackage: source changed by d3v1150m471c <d3v1150m471c@gmail.com>
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
rm -f splice.pyc
 dpkg-source -b splicepy-1.0
dpkg-source: warning: unknown information field 'Package' in input data in general section of control info file
dpkg-source: warning: unknown information field 'Version' in input data in general section of control info file
dpkg-source: warning: unknown information field 'Installed-Size' in input data in general section of control info file
dpkg-source: warning: unknown information field 'Architecture' in input data in general section of control info file
dpkg-source: warning: unknown information field 'Depends' in input data in general section of control info file
dpkg-source: warning: unknown information field 'Description' in input data in general section of control info file
dpkg-source: info: using source format `1.0'
dpkg-source: info: building splicepy in splicepy_1.0-0.tar.gz
dpkg-source: warning: missing information for output field Standards-Version
dpkg-source: info: building splicepy in splicepy_1.0-0.dsc
 debian/rules build
./splice.compile
 fakeroot debian/rules binary
dh binary
dh: Compatibility levels before 5 are deprecated.
   dh_auto_install
dh_auto_install: Compatibility levels before 5 are deprecated.
make[1]: Entering directory `/home/d3v11/Projects/SplicePY/splicepy-1.0'
mv splice.pyc /usr/bin/splice
mv: cannot move `splice.pyc' to `/usr/bin/splice': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/d3v11/Projects/SplicePY/splicepy-1.0'
dh_auto_install: make -j1 install DESTDIR=/home/d3v11/Projects/SplicePY/splicepy-1.0/debian/tmp returned exit code 2
make: *** [binary] Error 29
dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2
debuild: fatal error at line 1340:
dpkg-buildpackage -rfakeroot -D -us -uc failed

```

Oh, another thing ^^^, you may have noticed debuild is not detecting the original .tar.gz even though it's there...

---

