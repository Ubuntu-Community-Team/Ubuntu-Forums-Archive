---
title: "Can't install"
date: 2009-09-17
forum: General Help
---

### Post by v.mccann on 2009-09-17
What's going on? Anytime I try to add applications I get this:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I try typing that into the terminal but it doesn't work?

also synaptic package manager won't open. What do I do?

---

### Post by wojox on 2009-09-17
Try:

```
sudo apt-get -f install
```

Followed by:

```
sudo dpkg --configure -a
```

---

### Post by v.mccann on 2009-09-17
Worked. Thanks.

---

