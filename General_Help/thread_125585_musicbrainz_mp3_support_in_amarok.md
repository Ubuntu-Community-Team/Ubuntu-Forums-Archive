---
title: "musicbrainz mp3 support in amarok"
date: 2006-02-04
forum: General Help
---

### Post by dragonflyFZX on 2006-02-04
hi,

i am trying to use musicbrainz in amarok.  According to the wiki, i have to do this: 

Musicbrainz

    * Download and install MAD (libmad0)
    * Then rebuild and -install libtunepimp: 

apt-build --reinstall install libtunepimp2c2
apt-get install libtunepimp2c2 libtunepimp-bin


however, if i do so, it does not build, i am getting the following error:

```
-----> Building libtunepimp <-----
dpkg-buildpackage: source package is libtunepimp
dpkg-buildpackage: source version is 0.3.0-2ubuntu7
dpkg-buildpackage: source changed by root <root@localhost.localdomain>
dpkg-buildpackage: host architecture i386
 debian/rules clean
debian/rules:12: /usr/share/cdbs/1/class/autotools.mk: No such file or directory
debian/rules:13: /usr/share/cdbs/1/rules/debhelper.mk: No such file or directory
make: *** No rule to make target `/usr/share/cdbs/1/rules/debhelper.mk'.  Stop.
----> Cleaning up object files <-----
Cleaning in directory .
debian/rules:12: /usr/share/cdbs/1/class/autotools.mk: No such file or directory
debian/rules:13: /usr/share/cdbs/1/rules/debhelper.mk: No such file or directory
make: *** No rule to make target `/usr/share/cdbs/1/rules/debhelper.mk'.  Stop.
debuild: fatal error at line 836:
couldn't exec debian/rules:
Error while building libtunepimp2c2!
Sorry, no package to install.
Segmentation fault
bjvca@dragonfly:~$      
```

what could be the problem?

---

### Post by arosboro on 2007-12-31
All you need to do is install tunepimp-mp3 and then restart amarok:

[http://www.howtogeek.com/howto/ubuntu/fix-amarok-error-fingerprinting-of-mp3-files-is-not-supported/](http://www.howtogeek.com/howto/ubuntu/fix-amarok-error-fingerprinting-of-mp3-files-is-not-supported/)

---

