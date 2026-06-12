---
title: "kdict or dictionary for kde4"
date: 2012-06-22
forum: General Help
---

### Post by nozarm on 2012-06-22
I installed kdict_3.5.10-0ubuntu1~hardy2_i386.deb

but got the runtime error: 
kdict: error while loading shared libraries: libkio.so.4: cannot open shared object file: No such file or directory

locate libkio give me:
/usr/lib/libkio.so.5
/usr/lib/libkio.so.5.8.0

So I have a newer version of libkio installed since I have just upgraded my distribution to 12.04.  

How does one get around this issue?  And why has kdict dropped in 12.04?  I feel there are way too many changes in between distribution upgrades and not all favourable to the users. 

Another odditiy I experienced is that I could not find g77 in the 12.04 (precise pangolin) and I could not compile the fortran software using gfortran.  So I had to install g77 (gcc version 3.4.6) from an older distribution as well.  That, fortunately worked!


cheers,
Mina

---

### Post by howefield on 2012-06-22
Post spliced off to its own thread.

---

