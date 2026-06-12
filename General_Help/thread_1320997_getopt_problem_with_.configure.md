---
title: "getopt problem with ./configure"
date: 2009-11-09
forum: General Help
---

### Post by dougalkerr on 2009-11-09
Trying to ./configure a tar file and the configure almost finishes but displays 'getopt is missing but required'.
Can someone explain what is needed here.
Thanks.

---

### Post by michy99 on 2009-11-09
getopt is provided by the package gnulib.```
sudo apt-get install gnulib
```

---

### Post by dougalkerr on 2009-11-14
Thanks for the reply. Now what is meant by the last two lines when installing the package gnulib;

'Ignoring install-info called from maintainer script
The package gnulib should be rebuild with new debhelper to get trigger support'

How do I rebuild as asked. I am still very unfamiliar with a lot of this. Do I need to rebuild?

Thanks again.

---

