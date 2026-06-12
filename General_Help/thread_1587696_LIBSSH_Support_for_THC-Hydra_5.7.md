---
title: "LIBSSH Support for THC-Hydra 5.7"
date: 2010-10-04
forum: General Help
---

### Post by zuyx on 2010-10-04
Alright, so I downloaded the tar ball from the site.
compiled it all fine. 

But when I try to run the line 
```

./hydra -C Combo001.txt 10.0.6.100 ssh2
```

I end with 
```

Error: Compiled without LIBSSH support, module not available.
```

./configure gives the following, and I see nothing wrong since it says ssh is found.

```
medusa@Cerberus:~/Desktop/hydra-5.7-src$ sudo ./configure

Starting hydra auto configuration ...

Checking for openssl (libssl/ssl.h) ...
                                    ... found
Checking for Postgres (libpq.so) ...
                                 ... NOT found, module postgres disabled
Checking for SVN (libsvn_client-1 libapr-0.so libaprutil-0.so) ...
                              ... NOT found, module svn disabled
Checking for firebird (libfbclient.so) ...
                                       ... NOT found, module firebird disabled
Checking for NCP (libncp.so / nwcalls.h) ...
                                         ... NOT found, module NCP disabled
Checking for SAP/R3 (librfc/saprfc.h) ...
                                      ... NOT found, module sapr3 disabled
Get it from http://www.sap.com/solutions/netweaver/linux/eval/index.asp
Checking for libssh (libssh/libssh.h) ...
                                      ... found
NOTE: ensure that you have libssh v0.4.x installed!! Get it from http://www.libssh.org !
Checking for GUI req's (pkg-config) ...
                                    ... found

Hydra will be installed into .../bin of: /usr/local
  (change this by running ./configure --prefix=path)

Writing Makefile.in ...
now type "make"

```

---

### Post by zuyx on 2010-10-04
Anyone please

---

### Post by mons_i on 2010-10-04
> **zuyx said:**
> Anyone please
I know this is really late but for any future viewers of this post I found something that seemed to help resolve this situation.  I was getting the exact same error as described above and simply installing libssh-dev solved the problem on my ubuntu macahine:  10.04 LTS - Lucid Lynx

2 references for this and similar issues:
libssh - [http://wiredbytes.com/node/23](http://wiredbytes.com/node/23)
additional errors - [http://ubuntuforums.org/archive/index.php/t-927436.html](http://ubuntuforums.org/archive/index.php/t-927436.html)

---

### Post by zuyx on 2010-10-05
We already have that installed and still getting the error.

---

### Post by david.maciejak on 2010-10-19
Maybe it´s not the right lib, try installing libssh2-1-dev and libssh2-1. Do you find error during the make ?
thc-hydra 5.8 is available at [http://freeworld.thc.org/thc-hydra/](http://freeworld.thc.org/thc-hydra/) but i don´t think it will solve your issue

---

### Post by zakiakhmad on 2011-08-18
Dear Zuyx, 

have you tried run make clean to uninstall the previuos not-supported ssh hydra? After that, try to re-install hydra with libssh-dev installed.

Hope it will work!

---

### Post by BigBananaMan on 2011-09-05
I was having the same problem.  I compiled and then realized I forgot libssh when I tried to run it against my router so I installed it and recompiled; still it was not working.  
I tried "make clean" as you suggested, zakiakhmad and it worked like a charm.  Thank you.  I'll have to remember to make clean the next time I bork a compile.

---

