---
title: "Cannot install libogg-dev"
date: 2012-05-30
forum: General Help
---

### Post by yanom on 2012-05-30
I need the package libogg-dev, but I can't install it. Here is the error it gives me:

```
sudo apt-get install libogg-dev
```
```
  Depends on: libogg0 (=1.2.2~dfsg-1ubuntu1) but will install 1.2.2~dfsg-1ubuntu2
```

---

### Post by yanom on 2012-05-30
bump

---

### Post by raja.genupula on 2012-05-30
now try as ```
sudo apt-get install -f
```

or look for that in synaptic and try again .:)

---

