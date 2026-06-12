---
title: "Errors when trying to install gpart from tar.gz"
date: 2010-03-04
forum: General Help
---

### Post by mango_cake on 2010-03-04
Hi,

I'm currently trying to install gpart on Ubuntu. Problem is, I'm completely new to this whole Linux thing and I keep getting errors I don't understand.

So far I've extracted the tar.gz file, using the line "tar xvf gpart-0.1h.tar.gz".

According to the instruction file, a configure script is not necessary. It just says to "type 'make', if no error were encountered type 'make install' "

Well, after typing "make" I get a ton of errors. I don't really understand it. I've typed the "errors" section here:

gpart.c:72: warning: built-in function 'log' declared as non-function
In file included from /usr/include/fcntl.h:217
                 from gpart.c:52:
In function 'open',
    inlined from 'main' at gpart.c:1224:
/usr/include/bits/fcntl2.h:51: error: call to '__open_missing_mode' declared with attribute error: open with 0_CREAT in second argument needs 3 arguments
make[1]: *** [gpart.o] Error 1
make[1]: Leaving directory '/home/ubuntu/Documents/gpart-0.1h.src'
make:  *** [gpart] Error 2




I'd greatly appreciate any help, thank you!

---

### Post by mango_cake on 2010-03-04
Oh, forgot to mention, the install file also mentions that "it should compile under Linux and FreeBSD using GNU cc and GNU make."

I just downloaded the most recent Ubuntu available from the website, not sure if it's the right make?

---

