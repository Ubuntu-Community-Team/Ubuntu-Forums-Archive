---
title: "How do you compile upstream source into a .deb?"
date: 2009-07-31
forum: General Help
---

### Post by s3a on 2009-07-31
I have obtained backintime-0.9.26_src.tar.gz (not because there is no .deb available for it but because I want to learn how to make my own .deb).

Here is what I know and I believe I a missing a little bit of knowledge:

deniz@debian:~$ cd /home/deniz/Desktop/backintime_temp
deniz@debian:~/Desktop/backintime_temp$ tar xzf *
deniz@debian:~/Desktop/backintime_temp$ ls
backintime-0.9.26  backintime-0.9.26_src.tar.gz
deniz@debian:~/Desktop/backintime_temp$ cd backintime-0.9.26
deniz@debian:~/Desktop/backintime_temp/backintime-0.9.26$ dh_make --createorig

Type of package: single binary, multiple binary, library, kernel module or cdbs?
 [s/m/l/k/b] s

Maintainer name : Deniz Akcal
Email-Address   : deniz@debian 
Date            : Fri, 31 Jul 2009 06:20:22 -0400
Package Name    : backintime
Version         : 0.9.26
License         : blank
Using dpatch    : no
Type of Package : Single
Hit <enter> to confirm: 
[I]Currently there is no top level Makefile. This may require additional tuning.
Done. Please edit the files in the debian/ subdirectory now. You should also
check that the backintime Makefiles install into $DESTDIR and not in / .[/I]
deniz@debian:~/Desktop/backintime_temp/backintime-0.9.26$ dpkg-buildpackage
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: 
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package backintime
dpkg-buildpackage: source version 0.9.26-1
dpkg-buildpackage: source changed by Deniz Akcal <deniz@debian>
dpkg-buildpackage: host architecture amd64
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp configure-stamp
# Add here commands to clean up after the build process.
/usr/bin/make clean
make[1]: Entering directory `/home/deniz/Desktop/backintime_temp/backintime-0.9.26'
make[1]: *** No rule to make target `clean'.  Stop.
make[1]: Leaving directory `/home/deniz/Desktop/backintime_temp/backintime-0.9.26'
make: *** [clean] Error 2
dpkg-buildpackage: failure: fakeroot debian/rules clean gave error exit status 2
deniz@debian:~/Desktop/backintime_temp/backintime-0.9.26$

I put what I think is the issue in italic characters. But...what am I doing wrong? I have been trying to accomplish this for so many weeks now. I really can't afford to read hundreds of pages as previously suggested elsewhere. I feel it's pointless because I don't even end up understanding anything not to mention there is so much reading to do. If I am not mistaken, my issue involves debhelper as well as my rules file in the Debianized source directory. The problem is, I have no idea what to do or how to use anything.

Any help would be **GREATLY** appreciated!
Thanks in advance!

---

