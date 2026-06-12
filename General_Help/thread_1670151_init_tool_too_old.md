---
title: "init tool too old?"
date: 2011-01-18
forum: General Help
---

### Post by princeofnam on 2011-01-18
I tried to install the murrine engine but unfortunately I got this error while trying to ./configure the directory

> configure: error: Your intltool is too old.  You need intltool 0.37.1 or later.
sushi@Ragnarork:~/Downloads/murrine-0.98.1.1$ 

---

### Post by hawkmage on 2011-01-18
What version do you have installed?  Run this command to see:
```
apt-cache showpkg intltool
```

---

### Post by oldos2er on 2011-01-18
Why not install murrine from the repositories? ```
sudo apt-get install gtk2-engines-murrine
```

---

