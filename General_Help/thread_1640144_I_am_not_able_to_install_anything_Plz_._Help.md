---
title: "I am not able to install anything Plz . Help"
date: 2010-12-07
forum: General Help
---

### Post by asifnaz on 2010-12-07
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package abiword



what this error mean . Internet is working fine . How to fix this

---

### Post by gandaran on 2010-12-07
maybe you have to update software package list first
```
sudo apt-get update
```

---

### Post by karthick87 on 2010-12-07
What package you are trying to install?You may get that error if the package you are trying to install is not in the repositories.

First Try 
```
sudo apt-get update
```

if you get that error again,tell us the package name that you wanna install so that we can help you.

---

