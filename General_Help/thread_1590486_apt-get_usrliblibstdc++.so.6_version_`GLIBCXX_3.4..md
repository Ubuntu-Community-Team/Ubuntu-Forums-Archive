---
title: "apt-get: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by apt-"
date: 2010-10-07
forum: General Help
---

### Post by BrokenTrace on 2010-10-07
After the last ubuntu upgrade(using 10.04 Lucid) through the manager my system hosed up with the following error when trying to run apt-get:

/usr/lib$ apt-get
apt-get: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by apt-get)
apt-get: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by apt-get)
apt-get: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/lib/libapt-pkg-libc6.10-6.so.4.8)
apt-get: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/lib/libapt-pkg-libc6.10-6.so.4.8)
/usr/lib$

this is also preventing nautilus from starting. Any Ideas on how to fix this other than re-installing it. I have tried a few of the other suggestions on this fix to no avail. 

Thanks in advance.

---

### Post by xjesse on 2010-10-07
I found this thread. Maybe it will help?

[http://ubuntuforums.org/showthread.php?p=4806202]("http://ubuntuforums.org/showthread.php?p=4806202")

---

