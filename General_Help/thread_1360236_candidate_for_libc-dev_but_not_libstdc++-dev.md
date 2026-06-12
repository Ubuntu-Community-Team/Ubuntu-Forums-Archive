---
title: "candidate for libc-dev but not libstdc++-dev?"
date: 2009-12-20
forum: General Help
---

### Post by retval on 2009-12-20
Does anyone know why you can install the current standard C library by selecting "llibc-dev" but when you try and install C++'s library with "libstdc++-dev" you get

> 
Package libstdc++-dev is a virtual package provided by:
  libstdc++6-4.3-dev 4.3.4-5ubuntu1
  libstdc++6-4.2-dev 4.2.4-5ubuntu1
  libstdc++6-4.1-dev 4.1.2-27ubuntu1
  libstdc++6-4.4-dev 4.4.1-4ubuntu8
You should explicitly select one to install.
E: Package libstdc++-dev has no installation candidate


Is this a bug or a really lousy "feature"?

---

### Post by gordintoronto on 2009-12-20
It's a bug.

You might mention which version of Ubuntu this occurs in.  For example, in both Jaunty and Karmic, Synaptic does not offer libstdc++-dev.

---

