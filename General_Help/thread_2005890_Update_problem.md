---
title: "Update problem"
date: 2012-06-18
forum: General Help
---

### Post by angus1964 on 2012-06-18
When i started up ubuntu 12.04 today update manager made me aware there were 11 updates pending, mainly for unity 2d, but when i click install a message box comes up saying failed to download packages check your internet connection. My internet connection is working fine, anyone else having same problem?

---

### Post by plucky on 2012-06-18
> **angus1964 said:**
> When i started up ubuntu 12.04 today update manager made me aware there were 11 updates pending, mainly for unity 2d, but when i click install a message box comes up saying failed to download packages check your internet connection. My internet connection is working fine, anyone else having same problem?

Open a terminal and run ```
sudo apt update && sudo apt-get upgrade
``` and post back any errors.


Good Luck

---

### Post by NotSoRandomUsername on 2012-06-18
try apt-get autoremove.

---

### Post by angus1964 on 2012-06-18
```
sudo apt-get update && sudo apt-get upgrade 
```
Solved it.


Many Thanks

---

