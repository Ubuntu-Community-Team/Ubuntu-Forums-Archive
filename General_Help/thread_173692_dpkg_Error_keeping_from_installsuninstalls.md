---
title: "dpkg Error keeping from installs/uninstalls"
date: 2006-05-10
forum: General Help
---

### Post by boywondr16 on 2006-05-10
I've got some updates waiting to be installed, but I can't do anything with apt-get, Synaptic, or Update Manager because of this consistent message:

```
dpkg: parse error, in file `/var/lib/dpkg/status' near line 8407 package `avifile-xvid-plugin':
 `Depends' field, invalid package name `libavifile-0>7': character `>' not allowed - only letters, digits and -+._ allowed
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Thanks beforehand for the assistance...

---

### Post by Sef on 2006-05-10
From the Terminal/Konsole, have you tried this:

dpkg --configure -a

---

### Post by boywondr16 on 2006-05-10
I did, and get this message:

```
dpkg: parse error, in file `/var/lib/dpkg/status' near line 8407 package `avifile-xvid-plugin':
 `Depends' field, invalid package name `libavifile-0>7': character `>' not allowed - only letters, digits and -+._ allowed

```

I've tried sudo apt-get remove -f avifile-xvid-plugin and get the same message.  Same with attempting to force a libavifile-0>7 removal.

](*,)

---

