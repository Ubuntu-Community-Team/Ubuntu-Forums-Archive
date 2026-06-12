---
title: "Debug many broken Libraries, cause unknown, solution unknown!"
date: 2012-10-09
forum: General Help
---

### Post by jimmylimm on 2012-10-09
Hi all,

I have an issue that needs resolving and I'd rather not start from scratch with a fresh install.

I'm trying to run executable applications from terminal using ./appname. Here is an example:

```
:~/$ mrview imagefile.mif
mrview: symbol lookup error: /usr/local/lib/libgsl.so.0: undefined symbol: cblas_dnrm2
```

and

```
:~/dtk$ ./dtk
./dtk: error while loading shared libraries: libtiff.so.3: cannot open shared object file: No such file or directory
```

The issue is definitely related to shared libraries and dynamic links. I'm not sure how to debug these errors and am linux compitent but unfortunately do not know what has broken these libraries or links.

Any help to debug would be appreciated.

---

### Post by jimmylimm on 2012-10-09
Hold on... hold on...

Forgot to mention, am using Ubuntu 12.04, all upgrades done all updates done.

I've Just tried running these apps on a fresh install. the mrview one works. However the ./dtk does not!

I've tried installing libtiff4, however it just says it's already installed. cannot find the lib .so file anywhere.

Hope more info helps solve the issue!

thanks in advance ppl

---

