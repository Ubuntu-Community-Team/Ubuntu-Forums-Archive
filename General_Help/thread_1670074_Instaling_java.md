---
title: "Instaling java"
date: 2011-01-18
forum: General Help
---

### Post by BradNowacki on 2011-01-18
so how do i install Java on Ubuntu server?

---

### Post by 3Miro on 2011-01-18
If you have a graphical environment installed, you can use either the Software Center or Synaptic Package Manager (look for Sun Java).

If you have the command line only, you can use:
```
sudo apt-get search something
```
(replace something with java or whatever other word you want). This will search for all the possible programs that have "something" in their name. To install a specific program:
```
sudo apt-get install package-name
```

---

### Post by Chesamo on 2011-01-18
```
sudo apt-get install openjdk-6-jre
```

---

