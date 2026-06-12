---
title: "squid and apt-get"
date: 2010-01-15
forum: General Help
---

### Post by ant2ne on 2010-01-15
I noticed that my squid proxy breaks apt-get update with an error similar to
```
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)
```
Bypassing the proxy allows apt-get to update and fetch programs and all of that. So I can only assume that apt-get uses a port that squid isn't recognizing and I need to add that port. Any ideas?

Also, I'd like for squid to be able to cache apt-get programs. So every time I want to apt-get install openssh-server it just grabs it from my webcache. Any advice on that?

---

### Post by ant2ne on 2010-01-19
bump

nobody knows?

---

