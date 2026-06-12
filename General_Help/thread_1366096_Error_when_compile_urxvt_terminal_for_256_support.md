---
title: "Error when compile urxvt terminal for 256 support"
date: 2009-12-28
forum: General Help
---

### Post by Yumyai on 2009-12-28
Hi.

I followed the guide here and got error at last step
[http://scie.nti.st/2008/10/13/get-rxvt-unicode-with-256-color-support-on-ubunut](http://scie.nti.st/2008/10/13/get-rxvt-unicode-with-256-color-support-on-ubunut)

```

 fakeroot debian/rules clean
make[1]: *** No rule to make target `distclean'.  Stop.
make: [clean] Error 2 (ignored)
make[1]: *** No rule to make target `realclean'.  Stop.
make: [clean] Error 2 (ignored)
 dpkg-source -b rxvt-unicode-9.06
dpkg-source: warning: ignoring deletion of file config.sub
dpkg-source: warning: ignoring deletion of file config.guess
 debian/rules build
config.status: WARNING:  Makefile.in seems to ignore the --datarootdir setting
config.status: WARNING:  doc/Makefile.in seems to ignore the --datarootdir setting
background.C: In member function &#8216;bool bgPixmap_t::set_geometry(const char*)&#8217;:
background.C:273: error: invalid conversion from &#8216;const char*&#8217; to &#8216;char*&#8217;
background.C:274: error: invalid conversion from &#8216;const char*&#8217; to &#8216;char*&#8217;
background.C: In member function &#8216;bool bgPixmap_t::set_file(const char*)&#8217;:
background.C:680: error: invalid conversion from &#8216;const char*&#8217; to &#8216;char*&#8217;
make[2]: *** [background.o] Error 1
make[1]: *** [all] Error 1
make: *** [build-stamp] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
```


Anybody has this problem ?  I tried google it but it seems like noone got this problem.

---

