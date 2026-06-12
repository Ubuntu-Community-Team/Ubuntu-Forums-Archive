---
title: "updating gnu compiler collection"
date: 2012-01-22
forum: General Help
---

### Post by duchess767 on 2012-01-22
hello.  i am on ubuntu 10.04 and i need help updating my gcc.  right now when i do:

```

gcc -v

```it says it's version 4.4.3 when 4.6.x is the current version.  i would like to update it to the latest.  i downloaded the gcc4.6 from svn into a folder and i tried doing

```

./configure

``````

make

``````

make install

```but there is no makefile.  so i tried to use the package manager and it said it updated it but it didn't.  i am new to ubuntu so i need help.  thanks.

---

### Post by xyzzyman on 2012-01-23
[http://buildall.wordpress.com/2011/04/20/installing-gcc-4-6-in-the-ubuntu-10-10/](http://buildall.wordpress.com/2011/04/20/installing-gcc-4-6-in-the-ubuntu-10-10/)

Just make the appropriate changes in lines depending on the name of the tarball you download.

Are you trying to update as you actually will be compiling programs, or are you just updating for the sake of updating?

---

