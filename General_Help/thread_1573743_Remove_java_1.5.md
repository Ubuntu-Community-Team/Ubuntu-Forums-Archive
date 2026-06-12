---
title: "Remove java 1.5"
date: 2010-09-13
forum: General Help
---

### Post by vector on 2010-09-13
Hi all 
Having some difficulty installing jre6. It installs (synaptec_ but when I ask java -version at the cli it says 1.5.
 I tried a dpkg purge  of java but that did not seem to work either, possibly got the wording  wrong. I found something similar and adapted it.


```
sudo dpkg --list |grep "java" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

maybe in the distant past it was installed not using dpkg/ i cant recall.
But I need to get rid of it now please.

---

### Post by philinux on 2010-09-13
```
sudo update-alternatives --config java
```

---

### Post by vector on 2010-09-13
aahhh so simple thanks heaps Phill

---

