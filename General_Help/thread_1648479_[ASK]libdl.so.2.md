---
title: "[ASK]libdl.so.2"
date: 2010-12-18
forum: General Help
---

### Post by appzone on 2010-12-18
what is libdl.so.2 ?
can any one explain it to me?

when i trying to install .bin package, it's get error

```
/lib/tls/i686/cmov/libdl.so.2: version `' not found (required by 
```

---

### Post by appzone on 2010-12-19
anybody can help me?

---

### Post by I'mGeorge on 2010-12-19
it's a shared library part of the libc6 package. Try this 
```
sudo apt-get install libc6 libc6-dev
```
and after it try installing that bin file again

---

