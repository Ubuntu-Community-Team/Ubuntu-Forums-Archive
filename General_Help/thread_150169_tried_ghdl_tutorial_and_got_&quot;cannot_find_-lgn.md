---
title: "tried ghdl tutorial and got &quot;cannot find -lgnat-3.4&quot;"
date: 2006-03-25
forum: General Help
---

### Post by wfjm on 2006-03-25
Installed ghdl, tried the simple 'Hello Word' tutorial example from   [http://ghdl.free.fr/ghdl/index.html](http://ghdl.free.fr/ghdl/index.html) and got

```
ghdl -a hello.vhdl
ghdl -e hello_world
/usr/bin/ld: cannot find -lgnat-3.4
collect2: ld returned 1 exit status
```

libgnat is installed, the file is under /usr/lib/libgnat-3.4.so.1 .

Has somebody an idea on what is going wrong here ?

---

