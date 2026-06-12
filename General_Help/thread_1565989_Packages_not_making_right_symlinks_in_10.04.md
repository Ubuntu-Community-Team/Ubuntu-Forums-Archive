---
title: "Packages not making right symlinks in 10.04"
date: 2010-09-01
forum: General Help
---

### Post by stair314 on 2010-09-01
Just got a new machine today and installed Ubuntu 10.04.1 on it, starting from a blank hard drive.
I installed a bunch of packages related to my programming work with apt-get, and I found a bunch of problems:
> 
$ ls -l /usr/lib | grep libGL | grep -v GLU
-rw-r--r--  1 root root      654 2010-09-01 18:25 libGL.la
lrwxrwxrwx  1 root root       13 2010-09-01 18:55 libGL.so -> mesa/libGL.so
lrwxrwxrwx  1 root root       15 2010-09-01 18:25 libGL.so.1 -> libGL.so.256.53
-rwxr-xr-x  1 root root   992328 2010-09-01 18:25 libGL.so.256.53

> 
$ ls -l /usr/lib/mesa/
total 4
-rw-r--r-- 1 root root 30 2010-04-29 01:51 ld.so.conf
lrwxrwxrwx 1 root root 10 2010-09-01 18:55 libGL.so -> libGL.so.1

Why are these symlink paths relative rather than absolute? And libGL.so in the mesa directory pointing to a non-existing mesa/libGL.so.1 or is it meaning to point to /usr/lib/libGL.so.1?

Next up was libXi, there was a libXi.so.6 but no libXi.so. Same problem with libXmu.

Does anyone know why my package manager is so uniformly failing to install anything correctly?

Thanks in advance

---

