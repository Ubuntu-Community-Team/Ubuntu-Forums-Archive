---
title: "LORCON will not ./configure in 9.04"
date: 2009-12-26
forum: General Help
---

### Post by U333 on 2009-12-26
My rig is Ubuntu 9.04, kernel 2.6.28-17, 32bit
I would like to (install) compile lorcon-current.tgz

When I run ./configure the error I receive is "Missing working linux wireless extensions".
However, wireless-tools, libiw-dev, libiw29, iw, etc. (v29-1.1ubuntu2) are installed.

I've searched the lorcon site and found no reasons why it will not install.

Anybody have any experience with this package?

Thanks for your help.

---

### Post by seeknet on 2010-02-04
hi,

i am facing the same problem. The solution can't be that difficult?

thx to everyone willing to help!

---

### Post by rnerwein on 2010-02-04
hi
may the librarys are not in the default search path.
try: export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/your_path_to_the_libs
ciao

---

### Post by Bachstelze on 2010-02-04
Please paste your configure.log.

---

