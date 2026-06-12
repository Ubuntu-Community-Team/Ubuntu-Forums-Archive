---
title: "Wengo fails to find existing libssl"
date: 2006-06-30
forum: General Help
---

### Post by mibadt on 2006-06-30
Hi,
While trying to install Wengo from Debian package (using dpkg -i) it aborted with the following error:

"wengophone depends on libssl0.9.7 (>= 0.9.7); however:
  Package libssl0.9.7 is not installed.
dpkg: error processing wengophone (--install):"


However, as the following shows libssl0.9.8 is already installed.
"root@Atlantis:/usr/lib# pwd
/usr/lib
root@Atlantis:/usr/lib# ls -l libssl*
-rw-r--r-- 1 root root 130844 2006-06-08 21:06 libssl3.so
-rw-r--r-- 1 root root 247488 2006-03-29 12:01 libssl.so.0.9.8"


Please advise.

TIA
:)

---

### Post by vjun on 2006-07-19
i have the same problem too. Anyone out there know the issue please help. Thanks! :confused:

---

### Post by tuomas404 on 2006-10-17
Install libssl0.9.7 from [http://packages.debian.org/stable/libs/libssl0.9.7]("http://packages.debian.org/stable/libs/libssl0.9.7")
Then install wengophone. Worked for me.

---

