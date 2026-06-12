---
title: "Problem in compilation"
date: 2009-08-11
forum: General Help
---

### Post by sprasanna on 2009-08-11
I tried compiling a source file and got this message...

"/usr/bin/ld: crt1.o: No such file: No such file or directory"

then i did this 

$sudo apt-get install libc6-dev

then getting this message

$ sudo apt-get install libc6-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libc6-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libc6-dev has no installation candidate

What next should I try? Can someine help me pls. 

Regards
Prasanna

---

### Post by DGortze380 on 2009-08-11
> **sprasanna said:**
> I tried compiling a source file and got this message...

"/usr/bin/ld: crt1.o: No such file: No such file or directory"

then i did this 

$sudo apt-get install libc6-dev

then getting this message

$ sudo apt-get install libc6-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libc6-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libc6-dev has no installation candidate

What next should I try? Can someine help me pls. 

Regards
Prasanna

Search through synaptic, there is another version of libc6-dev available.

or try 

```

sudo apt-get install libc[tab][tab]

```

yes... actually press the tab key

---

