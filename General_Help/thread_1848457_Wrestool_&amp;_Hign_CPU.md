---
title: "Wrestool &amp; Hign CPU"
date: 2011-09-22
forum: General Help
---

### Post by Kodeine on 2011-09-22
Salutations!

So a few days ago I was using Firefox to download a file over 1GB (happens when downloading large files only). When just after finishing having downloaded the file suddenly I hear my CPU going crazy and the computer going really slowly. I was trying out chromium at the time (which I now really like) and thought I'd just switch and never use Firefox to download files again. However it turns out not to be Firefox's fault. It also happens when using Chromium. I managed to open 'System monitor' and found that a process called 'wrestool' was although not using much CPU was using over 700MB of memory space. I ended the process and my computer quickly recovered.

What is this 'wrestool' and why mite it be doing this?

Thanks bye!

---

### Post by patryk77 on 2011-09-22
Wrestool is a tool to extract resources (Icons) from Windows executables.

Below you can see how I figured it out ;)

locate to find the binary, dpkg to find which package it belongs to, apt-cache to get the package info and finally the manpage to get a description of that one tool:

You can get [more info on apt-cache on my blog (link).](http://glog.procrasstination.com/index.php?/archives/30-HOWTO-Ubuntu-Debian-package-management-apt-cache.html)

```
root@bt:/tmp# locate wrestool
/usr/bin/wrestool
/usr/share/man/man1/wrestool.1.gz
root@bt:/tmp# dpkg -S /usr/bin/wrestool 
icoutils: /usr/bin/wrestool
root@bt:/tmp# apt-cache show icoutils
Package: icoutils
Priority: optional
Section: graphics
Installed-Size: 252
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 0.29.1-0ubuntu1~lucid
Depends: libc6 (>= 2.8), libpng12-0 (>= 1.2.13-4), zlib1g (>= 1:1.1.4), perl, libwww-perl
Suggests: libterm-readline-gnu-perl | libterm-readline-perl-perl
Filename: pool/main/i/icoutils/icoutils_0.29.1-0ubuntu1~lucid_amd64.deb
Size: 76560
MD5sum: 83fadde316cf383e094c2098ee79ffdc
SHA1: 499acbb6fd44e74fa753031ab532e6b5399c78fe
SHA256: a08010240105bc356ae9fb0f15adc37ae95136dac291e402f4ad9732a1c31c36
Description: Create and extract MS Windows icons and cursors
 Icoutils is a set of programs that deal with MS Windows icons and
 cursors. Resources such as icons and cursors can be extracted from MS
 Windows executable and library files with "wrestool". Conversion of
 these files to and from PNG images is done with "icotool". "extresso"
 automates these tasks with the help of special resource scripts.
 .
 This package can be used to create "favicon.ico" files for web sites.
Homepage: http://www.nongnu.org/icoutils/
Original-Maintainer: Colin Watson <cjwatson@debian.org>

Package: icoutils
Priority: optional
Section: graphics
Installed-Size: 200
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 0.26.0-4ubuntu1
Depends: libc6 (>= 2.8), libpng12-0 (>= 1.2.13-4), zlib1g (>= 1:1.1.4), perl, libwww-perl
Suggests: libterm-readline-gnu-perl | libterm-readline-perl-perl
Filename: pool/main/i/icoutils/icoutils_0.26.0-4ubuntu1_amd64.deb
Size: 73304
MD5sum: 1256610d78420a77dde6625594fd0f9d
SHA1: e0c749d4600d13920c093fa2972434c8501c4371
SHA256: 4236e2daf84f6bef83ae570aecbec7a8f121896eb492fa68012965fb4b7c2923
Description: Create and extract MS Windows icons and cursors
 Icoutils is a set of programs that deal with MS Windows icons and
 cursors. Resources such as icons and cursors can be extracted from MS
 Windows executable and library files with "wrestool". Conversion of
 these files to and from PNG images is done with "icotool". "extresso"
 automates these tasks with the help of special resource scripts.
 .
 This package can be used to create "favicon.ico" files for web sites.
Original-Maintainer: Colin Watson <cjwatson@debian.org>

root@bt:/tmp# man wrestool
root@bt:/tmp# 

```

---

