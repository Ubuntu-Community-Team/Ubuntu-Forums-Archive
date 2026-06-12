---
title: "Updating Problem"
date: 2009-09-13
forum: General Help
---

### Post by dip huda on 2009-09-13
[B]I installed Ubuntu 9.04 yesterday. While updating, it shows following problem. 


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources.bz2)  Hash Sum mismatch

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources.bz2](http://bd.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources.bz2)  Hash Sum mismatch

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages.bz2](http://bd.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages.bz2)  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.[/B]


Anyone please help me.

---

### Post by zvacet on 2009-09-13
Probably you just have to refresh your source list.Applications>accessories>terminal and type

```
sudo apt-get update && sudo apt-get upgrade
```

---

