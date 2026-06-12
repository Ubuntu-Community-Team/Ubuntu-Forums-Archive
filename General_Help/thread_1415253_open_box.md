---
title: "open box"
date: 2010-02-24
forum: General Help
---

### Post by pedrom169 on 2010-02-24
When a new version of open box comes out. If compile a newer version of open box will it install over the current version or will it install a separate version?

---

### Post by bodhi.zazen on 2010-02-24
IMO it is best to compile into /usr/local 

you do this when you compile:

./configure --prefix=/usr/local
make
sudo make install

---

### Post by Bachstelze on 2010-02-24
> **bodhi.zazen said:**
> IMO it is best to compile into /usr/local 

you do this when you compile:

./configure --prefix=/usr/local
make
sudo make install

Or even better, make a DEB package of it (using checkinstall if you're lazy).

---

