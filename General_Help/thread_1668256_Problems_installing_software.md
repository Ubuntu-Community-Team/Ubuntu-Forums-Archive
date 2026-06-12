---
title: "Problems installing software"
date: 2011-01-16
forum: General Help
---

### Post by Crux_Dissimilata on 2011-01-16
I am trying to install OpenVAS but I'm getting some error here:
```
My@Machiner:/opt/OpenVas/openvas-libraries-3.0.0$ sudo make
cd base && cmake -DCMAKE_INSTALL_PREFIX=/usr/local -DSYSCONFDIR=/usr/local/etc -DLOCALSTATEDIR=/usr/local/var -DHAVE_WMI=NO -DLIBDIR=/usr/local/lib && make
/bin/sh: cmake: not found
make: *** [all] Error 127
```

---

### Post by sanderd17 on 2011-01-16
try
```

sudo apt-get install cmake

```

---

