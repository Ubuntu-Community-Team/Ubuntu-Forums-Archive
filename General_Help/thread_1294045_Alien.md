---
title: "Alien"
date: 2009-10-17
forum: General Help
---

### Post by RedSingularity on 2009-10-17
Hey everyone, i am having a problem with alien.  I have tryed converting 2 packages to .deb but get a similar error every time.  I will post the output.  

```
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
        xargs -0 -r -i cp -a {} debian/4l
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: failure: no dependency information found for /usr/lib/liblightscribe.so.1 (used by debian/4l/usr/4L/4L-cli).
dh_shlibdeps: command returned error code 512
make: [binary-arch] Error 1 (ignored)
dh_gencontrol
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: `4L-1.0': No such file or directory

```

Any ideas on this one?

---

### Post by beastrace91 on 2009-10-18
I am guessing by your sig & the error message that you are using a 64bit version of Ubuntu? If so what are the arch of the rpms you are trying to convert? From my guess it looks like the are i386 - if so go grab the 64bit rpms and then try to convert them.

~Jeff

---

### Post by RedSingularity on 2009-10-18
Ahh ok that makes scene.  Thanks.

---

