---
title: "&quot;ImportError: No module named lsb_release&quot; when installing 32bit libs"
date: 2011-11-14
forum: General Help
---

### Post by Rime2 on 2011-11-14
I'm testing 32 bit code on a 64 bit Ubuntu 11.0.4 system.  I started off by installing Python 2.7.2.  Next step is to install ia32-libs, and that's where I run into trouble :

root@vm1:/tmp/py/Python-2.7.2# apt-get install ia32-libs
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  lib32asound2 lib32bz2-1.0 lib32gcc1 lib32ncurses5 lib32ncursesw5
  lib32stdc++6 lib32v4l-0 lib32z1 libasound2 libc6-i386 libpython2.7
(snip)
Setting up lib32ncursesw5 (5.7+20101128-1) ...
Setting up ia32-libs (20090808ubuntu13) ...
Traceback (most recent call last):
  File "/usr/bin/lsb_release", line 26, in <module>
    import lsb_release
ImportError: No module named lsb_release
[: 11: =: unexpected operator
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

/usr/bin/lsb_release exists, but if I try to run it :

root@vm1:/tmp/py/Python-2.7.2# /usr/bin/lsb_release
Traceback (most recent call last):
  File "/usr/bin/lsb_release", line 26, in <module>
    import lsb_release
ImportError: No module named lsb_release

I've tried adding/removing lsb_release and the libraries, but it doesn't help.    Any suggestions ?

Thanks !

---

