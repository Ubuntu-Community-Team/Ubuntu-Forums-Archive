---
title: "Issue Building libvalhalla 2.0 from Source to .deb"
date: 2011-01-11
forum: General Help
---

### Post by beastrace91 on 2011-01-11
So I am trying to package up the latest version of [Enna]("http://enna.geexbox.org/") media center to .deb form on Lucid. In order to do so I first need to package up [libvalhalla]("http://libvalhalla.geexbox.org/") >= 2.0

Everything is going well, I get my debian folder all setup, control file and rules setup and then when I go to build the package I it fails out this this error message:

```
dpkg-buildpackage -rfakeroot
dpkg-buildpackage: warning: using a gain-root-command while being root
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package libvalhalla
dpkg-buildpackage: source version 2.0.0-1
dpkg-buildpackage: source changed by Jeff Hoogland <jeffhoogland@linux.com>
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
dh  clean
   dh_testdir
   dh_auto_clean
   dh_clean
 dpkg-source -b libvalhalla-2.0.0
dpkg-source: info: using source format `1.0'
dpkg-source: info: building libvalhalla using existing libvalhalla_2.0.0.orig.tar.gz
dpkg-source: info: building libvalhalla in libvalhalla_2.0.0-1.diff.gz
dpkg-source: info: building libvalhalla in libvalhalla_2.0.0-1.dsc
 debian/rules build
dh  build
   dh_testdir
   dh_auto_configure
Unknown option "--build=i486-linux-gnu".
See ./configure --help for available options.
dh_auto_configure: ./configure --build=i486-linux-gnu --prefix=/usr --includedir=${prefix}/include --mandir=${prefix}/share/man --infodir=${prefix}/share/info --sysconfdir=/etc --localstatedir=/var --libexecdir=${prefix}/lib/libvalhalla --disable-maintainer-mode --disable-dependency-tracking returned exit code 1
make: *** [build] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2

```

I am by no means an expert at packaging - anyone mind filling me in on why this is failing and how I can get it to actually build properly? I see it has to do with the "--build" option, but why is it passing this option and how can I stop it from doing so?

Cheers,
~Jeff

---

### Post by pinguy on 2011-01-11
[http://www.uluga.ubuntuforums.org/showpost.php?p=10275538&postcount=4](http://www.uluga.ubuntuforums.org/showpost.php?p=10275538&postcount=4)

---

### Post by beastrace91 on 2011-01-11
> **pinguy said:**
> [http://www.uluga.ubuntuforums.org/showpost.php?p=10275538&postcount=4](http://www.uluga.ubuntuforums.org/showpost.php?p=10275538&postcount=4)

Oh hai Pinguy.

That does not pertain to what I am trying to do as the Enlightenment binaries I am using are much newer than any thing that ships with pre-packaged copies of Enna.

Anyone have ideas why my build of libvalhalla isn't being successful?

~Jeff

---

