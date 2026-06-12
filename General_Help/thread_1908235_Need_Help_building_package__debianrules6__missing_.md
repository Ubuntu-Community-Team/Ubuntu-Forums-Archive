---
title: "Need Help building package : debian/rules:6: *** missing separator.  Stop."
date: 2012-01-13
forum: General Help
---

### Post by someitalian123 on 2012-01-13
I'm following this guide to build a dkms package for my wireless driver since it wasn't supported out of the box and I don't feel like manually recompiling it every time I upgrade the kernel.

[http://basilevsthecat.blogspot.com/2011/11/how-to-build-dkms-debian-package.html](http://basilevsthecat.blogspot.com/2011/11/how-to-build-dkms-debian-package.html)

My rules file looks like this

```
#!/usr/bin/make -f

VERSION=$(shell dpkg-parsechangelog |grep ^Version:|cut -d ' ' -f 2)

%:
 dh $@ --with dkms

override_dh_install:
 dh_install Makefile rt3562sta.c usr/src/rt3562sta-$(VERSION)/

override_dh_dkms:
 dh_dkms -V $(VERSION)
```

I keep getting this error

```
debian/rules:6: *** missing separator.  Stop.
dpkg-buildpackage: error: fakeroot debian/rules clean gave error exit status 2

```

---

