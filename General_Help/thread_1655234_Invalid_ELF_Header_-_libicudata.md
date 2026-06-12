---
title: "Invalid ELF Header - libicudata"
date: 2010-12-29
forum: General Help
---

### Post by rockerZ71 on 2010-12-29
I get this error when trying to launch software-center and openoffice (I'm sure more too, this is what I have noticed so far):

/lib/libicudata.so.42: invalid ELF header


This is on a recent install of 10.10 netbook remix, and I then installed xfce.

The library is there:

```
***********:~$ ls -la /usr/lib | grep icudata
lrwxrwxrwx   1 root root           18 Dec 29 11:09 libicudata.so -> libicudata.so.42.1
lrwxrwxrwx   1 root root           18 Dec 26 20:17 libicudata.so.42 -> libicudata.so.42.1
-rw-r--r--   1 root root     16011828 Nov 23  2009 libicudata.so.42.1
-rw-r--r--   1 root root          926 Nov 23  2009 libsicudata.a
```


any advice?  Thanks in advance

---

### Post by rockerZ71 on 2010-12-29
reinstalled libicu42 and it is fixed.

---

