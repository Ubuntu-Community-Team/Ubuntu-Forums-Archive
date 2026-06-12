---
title: "Problem installing JDK 1.5"
date: 2006-02-08
forum: General Help
---

### Post by rkakkar on 2006-02-08
I had downloaded the .bin file from Sun's site and then executed the following to create a debian package:

$ fakeroot make-jpkg jdk-1_5_0_05-linux-i586.bin

After showing me the usual license agreement etc., it threw the following error:

Unpacking...
Checksumming...
0
0
Extracting...
UnZipSFX 5.42 of 14 January 2001, by Info-ZIP (Zip-Bugs@lists.wku.edu).
  inflating: jdk-1_5_0_05-linux-i586.rpm
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - No such file or directory (2)
error: cannot open Packages database in /var/lib/rpm


Any ideas?  :confused:

---

