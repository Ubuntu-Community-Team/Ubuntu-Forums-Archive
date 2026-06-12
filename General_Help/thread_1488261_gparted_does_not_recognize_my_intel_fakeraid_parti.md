---
title: "gparted does not recognize my intel fakeraid partitions"
date: 2010-05-19
forum: General Help
---

### Post by cgb223 on 2010-05-19
hey Gparted does not recognize my intel ICH7 fake raid 0 partitions rendering it useless. Am I missing a package that will add this? I know the live disk can do this. Is it something to do with dmraid? 

using 10.04 64 bit ubuntu

Help would be appreciated

---

### Post by admo on 2011-03-03
Hi!
I have the same problem. Nobody knows the answer?

EDITED:
Ok, I know the answer. You should install kpartx package. This solves my problem.

---

### Post by bsntech on 2011-03-03
Correct.

You have to install the kpartx package which adds the appropriate modules for gparted to find any fakeraid devices.  Ensure you also have dmraid installed as well.

Brian S.
[http://www.bsntech.com]("http://www.bsntech.com")

---

