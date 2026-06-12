---
title: "command to see ubuntu version"
date: 2006-03-19
forum: General Help
---

### Post by FISH on 2006-03-19
i know redhad has this cat /etc/redhat-version does ubuntu have one?

---

### Post by Zelut on 2006-03-19
you can run variations of 'uname' to get version & kernel information.

uname -r (kernel)
uname -a (everything), etc..

EDIT: This doesn't seem to report on my 5.10 machine.  I was sure it did (it reports 'Dapper' on my test machine.

---

### Post by taurus on 2006-03-19
<Ctrl><Alt>F2.  To get back to your X, <Ctrl><Alt>F7.

---

### Post by Super Jamie on 2008-06-16
```
cat /etc/issue
```
```
cat /etc/lsb-release
```


```
cat /etc/apt/sources.list
``` is also a roundabout way of seeing what repositories the box is using, which should tell you the dist version

if your machine is mixing distro repos, apt pinning may be in effect, you can see if this is present with ```
cat /etc/apt/preferences
```

---

