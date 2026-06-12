---
title: "How To Solve A (Kind Of) Weird Dependency Issue"
date: 2011-09-18
forum: General Help
---

### Post by dniMretsaM on 2011-09-18
So I'm attempting to compile CClive 0.2.7 from and it requires libquvi. The problem is libquvi is in the repositories but it's named libquvi0, which doesn't register when I run the configure script. Ok, so I'll compile libquvi (I don't think the version if the repos is high enough anyway), but it has the same issue. It requires libcurl, but the package in the repos is libcurl3. I don't feel like compiling 6 programs (<- exaggeration) just to install CClive, so what can I do? Can I edit the configure scripts to accept the libraries in the repos? Also, why are the packages named that way? It would make more sense to me to name them without the numbers since it should be obvious that it causes dependency issues.

---

### Post by dniMretsaM on 2011-09-19
Bump.

---

### Post by ron999 on 2011-09-19
> **dniMretsaM said:**
> Bump.
Hi
_libcurl3 is OK_.

I've recently compiled quvi-0.2.19 and cclive-0.7.6

If you get bogged down, ask.:D

---

### Post by dniMretsaM on 2011-09-19
> **ron999 said:**
> Hi
_libcurl3 is OK_.

I've recently compiled quvi-0.2.19 and cclive-0.7.6

If you get bogged down, ask.:D

When I try to compile libquvi 0.2.19 I get this:
```
checking for libcurl... no
configure: error: Package requirements (libcurl >= 7.18.2) were not met:

No package 'libcurl' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables libcurl_CFLAGS
and libcurl_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```The first part is obviously telling me that I don't have libcurl installed (libcurl3 7.21.3 is installed). Not really sure what the second part means (about pkg-config stuff). I checked the man page as suggested, but I still don't get what it's asking me to do.

---

### Post by ron999 on 2011-09-19
> **dniMretsaM said:**
> 
The first part is obviously telling me that I don't have libcurl installed (libcurl3 7.21.3 is installed).
Hi
Look in Synaptic.
Check that these _four_ are installed:-
curl-7.21.3
libcurl3-7.21.3
libcul3-gnutls-7.21.3
libcurl4-gnutls-dev-7.21.3

---

### Post by dniMretsaM on 2011-09-19
Ok well that worked, but now it's asking for a package 'lua-5.1' which isn't in the repos. I installed these:
liblua5.1-event-dev
liblua5.1-event0
liblua5.1-socket2
liblua5.1-0

But that didn't help...

---

