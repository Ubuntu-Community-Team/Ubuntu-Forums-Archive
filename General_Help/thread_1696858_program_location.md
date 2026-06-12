---
title: "program location"
date: 2011-02-28
forum: General Help
---

### Post by Joe_Linux on 2011-02-28
How do I determine a programs location ?

---

### Post by zenwalker on 2011-02-28
What program your talking about??
In linux, most user based application executables are in /usr/bin and related files of that will be in /usr/lib/<App name folder>

For root user specific, in /usr/sbin

---

### Post by Vaphell on 2011-02-28
usually programs are in /usr/bin
```
whereis firefox
locate firefox | grep /bin/
```
| grep /bin/ filters out averything that doesn't match /bin/ in locate output

---

