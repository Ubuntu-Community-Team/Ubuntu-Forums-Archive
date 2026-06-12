---
title: "dpkg-source"
date: 2010-01-13
forum: General Help
---

### Post by frt975 on 2010-01-13
When I try building a source package for scribus I get this
```
 dpkg-buildpackage -rfakeroot -d -us -uc -S
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package scribus
dpkg-buildpackage: source version 1.3.5.1
dpkg-buildpackage: source changed by Flaviu Tamas <frt975@rocketmail.com>
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f configure-stamp build-stamp install-stamp
rm -rf /home/flaviu/src/scribus-1.3.5.1/debian/build /home/flaviu/src/scribus-1.3.5.1/debian/scribus
dh_clean
dpatch deapply-all
rm -rf patch-stamp debian/patched
 dpkg-source -b scribus-1.3.5.1
dpkg-source: info: using source format `1.0'
dpkg-source: info: building scribus in scribus_1.3.5.1.tar.gz
dpkg-source: warning: missing information for output field Maintainer
dpkg-source: info: building scribus in scribus_1.3.5.1.dsc
 dpkg-genchanges -S >../scribus_1.3.5.1_source.changes
dpkg-genchanges: including full source code in upload
dpkg-genchanges: error: missing information for critical output field Maintainer
dpkg-buildpackage: error: dpkg-genchanges gave error exit status 9
debuild: fatal error at line 1334:
dpkg-buildpackage -rfakeroot -d -us -uc -S failed

```My debian/ dictionary is attached

---

