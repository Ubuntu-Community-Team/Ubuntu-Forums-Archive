---
title: "sctp support"
date: 2011-07-18
forum: General Help
---

### Post by demiurg on 2011-07-18
Ubuntu is supposed to come with sctp support, right ? I have libsctp1 library installed, but I cannot find netinet/sctp.h include file... what am I missing ?

I know about the lksctp library, but before I install non-dep packages I'd like to figure out why it does not work out of the box.

---

### Post by gmargo on 2011-07-18
```

$ apt-cache search libsctp
libsctp-dev - user-space access to Linux Kernel SCTP - development files
libsctp1 - user-space access to Linux Kernel SCTP - shared library

```You are missing the **libsctp-dev** package - it contains the header files.

---

### Post by demiurg on 2011-07-18
Oops. This was obvious. Thanks

---

