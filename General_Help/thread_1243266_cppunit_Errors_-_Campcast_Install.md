---
title: "cppunit Errors - Campcast Install"
date: 2009-08-18
forum: General Help
---

### Post by Randem on 2009-08-18
Hi everyone,

I am trying to install Campcaster onto Ubuntu 9.04 Jaunty using the files I extracted from
campcaster-1.3.0.tar.bz2 and campcaster-libraries-1.3.0.tar.bz2

When I try *make install* I receive the following errors:

TypeInfoHelper.cpp:27: error: 'free' was not declared in this scope
make[4]: *** [TypeInfoHelper.lo] Error 1
make[4]: Leaving directory `/home/radioadmin/Desktop/campcaster-1.3.0/src/tools/cppunit/cppunit-1.10.2/tmp/cppunit-1.10.2/src/cppunit'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/home/radioadmin/Desktop/campcaster-1.3.0/src/tools/cppunit/cppunit-1.10.2/tmp/cppunit-1.10.2/src'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/radioadmin/Desktop/campcaster-1.3.0/src/tools/cppunit/cppunit-1.10.2/tmp/cppunit-1.10.2'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/radioadmin/Desktop/campcaster-1.3.0/src/tools/cppunit/cppunit-1.10.2'
make: *** [tmp/tools_setup.stamp] Error 2

I would appreciate any suggestions on how to resolve this issue.  Cheers.

---

### Post by nikhilk on 2009-08-18
I found .deb packages for Ubuntu on [SourceForge]("http://sourceforge.net/projects/campcaster/files/")
See if that works before installing it by compiling from source.

---

### Post by Randem on 2009-08-18
Thank you nikhilk.

The only available packages are for Dapper there is no package available for Jaunty.

---

### Post by Randem on 2009-08-18
As suggested, I tried to install Campcaster using the dapper_1.3.0-1 packages, but receive an
*Error: Dependency is not satisfiable: libboost-date-time1.33.1*

Installing libboost-date-time1.35.0 libraries did not resolve the problem. :(
Back to the installation from source code.

Does anyone have any suggestions on how to resolve the cppunit Errors?

As an alternative, I looked at the[FONT=Arial][COLOR=#9c0001][/COLOR][/FONT][COLOR=#000000] [Rivendell broadcast automation solution]("http://www.rivendellaudio.org/"); however, it seems that Rivendel works only with AudioScience audio cards.
[/COLOR]

---

### Post by EliotB on 2010-02-18
> **Randem said:**
> 
As an alternative, I looked at the[COLOR=#000000] [Rivendell broadcast automation solution]("http://www.rivendellaudio.org/"); however, it seems that Rivendel works only with AudioScience audio cards.
[/COLOR]
This was originally true, and it probably works best with AudioScience cards, however, it does now also work with any card that has an ALSA driver.
(disclaimer: I work for AudioScience)

---

