---
title: "Multi-arch dircectory / cmake problem"
date: 2011-11-30
forum: General Help
---

### Post by memecs on 2011-11-30
Hi, 

I just updated to 11.10 and now I can't compile anymore with cmake. Basically cmake is looking for a library in /usr/lib but the library is in /usr/lib/i386-linux-gnu. 

I re-installed cmake to the newest version (2.8.6) and the problem is not fixed yet. 

I know the quick fix would be to ln -s all the library back in /usr/lib but it really doesn't sound like a good solution...

---

