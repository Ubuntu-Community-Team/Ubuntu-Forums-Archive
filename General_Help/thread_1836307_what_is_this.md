---
title: "what is this?"
date: 2011-08-30
forum: General Help
---

### Post by vikash_chandola on 2011-08-30
see screen shot. what that want to say.Si that saying to update software center. 
I click repair but nothing happen.

---

### Post by akand074 on 2011-08-30
Open up a terminal and try:

```
sudo apt-get install -f
```if that doesn't work try these

```
sudo apt-get update
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
```

then try the install again

---

