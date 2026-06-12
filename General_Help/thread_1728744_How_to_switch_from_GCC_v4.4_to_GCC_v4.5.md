---
title: "How to switch from GCC v4.4 to GCC v4.5?"
date: 2011-04-14
forum: General Help
---

### Post by uqbar on 2011-04-14
As per default installation I have this:

~ ls -l /usr/bin | grep '4\.[45]'
lrwxrwxrwx 1 root   root           7 2011-04-13 11:13 cpp -> cpp-4.4
-rwxr-xr-x 1 root   root      224488 2010-09-27 20:41 cpp-4.4
-rwxr-xr-x 1 root   root      237008 2010-09-27 23:00 cpp-4.5
lrwxrwxrwx 1 root   root           7 2011-04-14 08:58 g++ -> g++-4.4
-rwxr-xr-x 1 root   root      228520 2010-09-27 20:42 g++-4.4
-rwxr-xr-x 1 root   root      236944 2010-09-27 23:01 g++-4.5
lrwxrwxrwx 1 root   root           7 2011-04-13 11:13 gcc -> gcc-4.4
-rwxr-xr-x 1 root   root      224488 2010-09-27 20:43 gcc-4.4
-rwxr-xr-x 1 root   root      232912 2010-09-27 23:03 gcc-4.5
lrwxrwxrwx 1 root   root           8 2011-04-13 11:13 gcov -> gcov-4.4
-rwxr-xr-x 1 root   root       30212 2010-09-27 20:43 gcov-4.4
-rwxr-xr-x 1 root   root       30216 2010-09-27 23:03 gcov-4.5
lrwxrwxrwx 1 root   root           7 2011-04-13 11:13 i686-linux-gnu-cpp -> cpp-4.4
lrwxrwxrwx 1 root   root           7 2011-04-13 11:13 i686-linux-gnu-cpp-4.4 -> cpp-4.4
lrwxrwxrwx 1 root   root           7 2011-04-14 08:56 i686-linux-gnu-cpp-4.5 -> cpp-4.5
lrwxrwxrwx 1 root   root           7 2011-04-14 08:58 i686-linux-gnu-g++ -> g++-4.4
lrwxrwxrwx 1 root   root           7 2011-04-13 18:50 i686-linux-gnu-g++-4.4 -> g++-4.4
lrwxrwxrwx 1 root   root           7 2011-04-14 08:58 i686-linux-gnu-g++-4.5 -> g++-4.5
lrwxrwxrwx 1 root   root           7 2011-04-13 11:13 i686-linux-gnu-gcc -> gcc-4.4
lrwxrwxrwx 1 root   root           7 2011-04-13 11:13 i686-linux-gnu-gcc-4.4 -> gcc-4.4
lrwxrwxrwx 1 root   root           7 2011-04-14 08:58 i686-linux-gnu-gcc-4.5 -> gcc-4.5

Is there a way to automatically switch from the default v4.4 to the newer v4.5?

I think I can still manually recrete the links, but am also afraid to leave something out.

---

