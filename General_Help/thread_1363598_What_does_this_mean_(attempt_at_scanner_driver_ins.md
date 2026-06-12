---
title: "What does this mean? (attempt at scanner driver install in terminal)"
date: 2009-12-24
forum: General Help
---

### Post by azitizz on 2009-12-24
Hi There Im wondering if the following log can be better interpreted by anyone else as Im still a beginner with Linux. Im trying to install a driver for a Canon MP510 multi printer/scanner as its not being detected and using xsane results in internet being cutoff for some reason.
 I followed the advice on downloading and rpm package and converting to deb using alien. I did this in terminal and below is what came of it. 
> error: incorrect format: unknown tag
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
xargs -0 -r -i cp -a {} debian/scangearmp-mp510
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dh_gencontrol
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: dpkg-gencontrol returned exit code 255
make: *** [binary-arch] Error 1
find: `scangearmp-mp510-1.00': No such file or directory 
There is a deb file now on my desktop but Im not sure what to do with it and if it is indeed the wrong "architecture" as is stated in the log. Is it because its made for 32 bit and I have a 64 bit?

---

### Post by 73ckn797 on 2009-12-24
You are trying to install a 32 bit driver into a 64 bit Ubuntu?

I am not familiar with Canon printers and whether they have drivers native in Ubuntu.

Did you check System/Administration/Hardware Drivers?

---

