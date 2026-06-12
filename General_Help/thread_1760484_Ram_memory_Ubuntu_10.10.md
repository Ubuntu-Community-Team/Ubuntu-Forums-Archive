---
title: "Ram memory Ubuntu 10.10"
date: 2011-05-17
forum: General Help
---

### Post by geeknutty on 2011-05-17
My machine a Dell PowerEdge SC 1425 running Ubuntu 10.10.
Ubuntu only recognize 3.4 Gb. of memory out of 12Gb.
Anything i can do to make it recognize the full 12gb.
thanks:D

---

### Post by tgm4883 on 2011-05-17
Sounds like you have the 32-bit version installed without PAE. Post the output of

```
uname -a
```

---

