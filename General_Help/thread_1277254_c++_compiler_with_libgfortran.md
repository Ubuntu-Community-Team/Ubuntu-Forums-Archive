---
title: "c++ compiler with libgfortran"
date: 2009-09-28
forum: General Help
---

### Post by solaris2000 on 2009-09-28
not sure whether this is the right place to ask..

I ve been stuck with this for days. I just switched to Ubuntu. While compiling with g++-4.3, i got a lot of things like this : undefined reference to `_gfortran_pow_r8_i4'; even those earlier compiled executable file can't work at all, when i run them, the same thing happens.

After searching on websites, i found it seemed to be a problem of g++ or gfortran.  some ppl recommended to use old g++-3.4. Well, i installed g++-3.4 then, but the old g++-3.4 can't find any library:
1.C:1:20: iostream: No such file or directory
1.C:2:19: fstream: No such file or directory

Im now completely out of mind what i can do next. I don't know, whether things are gonna work even if g++-3.4 gets the libs.

 ls -alt /usr/lib/libgfortran*
lrwxrwxrwx 1 root root     20 2009-09-26 19:59 /usr/lib/libgfortran.so.0 -> libgfortran.so.3.0.0
lrwxrwxrwx 1 root root     20 2009-09-26 06:13 /usr/lib/libgfortran.so.3 -> libgfortran.so.3.0.0
-rw-r--r-- 1 root root 728068 2009-03-16 20:29 /usr/lib/libgfortran.so.3.0.0


Thanks for any help

---

