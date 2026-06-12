---
title: "something strange happened to permissions"
date: 2010-05-05
forum: General Help
---

### Post by evouga on 2010-05-05
I recently upgraded to Lucid Lynx, but now several command-line programs no longer work. For instance:

> 
evouga@aristotle:~$ evince
evince: error while loading shared libraries: libz.so.1: failed to map segment from shared object: Permission denied
evouga@aristotle:~$ ls -l /usr/lib/libz.so 
lrwxrwxrwx 1 root root 20 2010-05-03 18:47 /usr/lib/libz.so -> /lib/libz.so.1.2.3.3
evouga@aristotle:~$ ls -l /lib/libz.so.1.2.3.3 
-rw-r--r-- 1 root root 92752 2009-11-09 10:53 /lib/libz.so.1.2.3.3
evouga@aristotle:~$ 

What could be the problem?

---

