---
title: "Package Intsallation Problem"
date: 2010-03-01
forum: General Help
---

### Post by masoodstar on 2010-03-01
I want to install the lbflow package (a kind of scientific one)

but I've got this error with the sudo make command.

Please help if you have any suggest or idea.

Thanks


make  all-recursive
make[1]: Entering directory `/home/group/lbflow-1.1'
Making all in src
make[2]: Entering directory `/home/group/lbflow-1.1/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I..        -g -O2 -MT lbflow-lbflow.o -MD -MP -MF ".deps/lbflow-lbflow.Tpo" -c -o lbflow-lbflow.o `test -f 'lbflow.cpp' || echo './'`lbflow.cpp; \
    then mv -f ".deps/lbflow-lbflow.Tpo" ".deps/lbflow-lbflow.Po"; else rm -f ".deps/lbflow-lbflow.Tpo"; exit 1; fi
In file included from lbflow.cpp:27:
parser.h:67: error: ‘uint’ does not name a type
make[2]: *** [lbflow-lbflow.o] Error 1
make[2]: Leaving directory `/home/group/lbflow-1.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/group/lbflow-1.1'
make: *** [all] Error 2

---

### Post by teward on 2010-03-01
Does this package not exist in the repositories?

---

### Post by -kg- on 2010-03-01
> **TrekCaptainUSA said:**
> Does this package not exist in the repositories?

No.  I first checked the repos and it doesn't exist.  I then looked up the software and, from [the website:]("http://www.dur.ac.uk/ed.llewellin/lbflow/downloads.htm")

> LBflow is not (yet) an open source project and the core executable is available only by request. Requests for academic use will always be granted, free of charge, subject to certain conditions regarding redistribution and collaboration / acknowledgement.

So naturally it would not exist in *any* repository, unless it is included in some esoteric science-related distribution, which isn't likely, since it is not FOSS (yet).

---

### Post by masoodstar on 2010-03-02
Exactly you're right and this software has not been FOSS yet.

I want to solve this problem with that package which I attached the error.

Do U have any idea?

---

### Post by masoodstar on 2010-06-02
Is there anyone experienced with this kind of errors (make error)?

Any useful help would be appreciated.

Thanks.
[SIZE=2][B]
group@group-desktop:~/lbflow-1.1$ make
make  all-recursive
make[1]: Entering directory `/home/group/lbflow-1.1'
Making all in src
make[2]: Entering directory `/home/group/lbflow-1.1/src'
source='lbflow.cpp' object='lbflow-lbflow.o' libtool=no \
    DEPDIR=.deps depmode=none /bin/bash ../depcomp \
    g++ -DHAVE_CONFIG_H -I. -I. -I..         -c -o lbflow-lbflow.o `test -f 'lbflow.cpp' || echo './'`lbflow.cpp
In file included from lbflow.cpp:27:
parser.h:67: error: ‘uint’ does not name a type
make[2]: *** [lbflow-lbflow.o] Error 1
make[2]: Leaving directory `/home/group/lbflow-1.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/group/lbflow-1.1'
make: *** [all] Error 2
[/B][/SIZE]

---

