---
title: "archi of my PC"
date: 2010-03-30
forum: General Help
---

### Post by nischalinn on 2010-03-30
What are the commands to know the complete architecture of my PC and of microprocessor?

---

### Post by marshmallow1304 on 2010-03-30
```
sudo lshw -C CPU | grep width
```
will tell you if your processor is 32 or 64 bit.

For more processor information, see
```
sudo lshw -C CPU
```
and
```
cat /proc/cpuinfo
```

To see the architecture of the installed Linux, use
```
uname -m
```

---

