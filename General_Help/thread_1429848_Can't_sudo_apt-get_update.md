---
title: "Can't sudo apt-get update"
date: 2010-03-14
forum: General Help
---

### Post by TheNessus on 2010-03-14
W: GPG error: [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CF

weird.

---

### Post by oldos2er on 2010-03-14
```
wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
```

---

### Post by TheNessus on 2010-03-15
> **oldos2er said:**
> ```
wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
```
thanks :)
I took the chance though to reinstall my deformed system :)

---

