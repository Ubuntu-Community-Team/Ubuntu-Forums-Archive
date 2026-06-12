---
title: "Need a Terminal Command."
date: 2010-06-20
forum: General Help
---

### Post by warfacegod on 2010-06-20
Can someone please post the code for clearing RAM as cache?

Thanks in advance.

---

### Post by Zip247 on 2010-06-20
check [this]("http://ubuntuforums.org/showthread.php?t=589975") thread

on the 2nd page is where they talk about lucid

I also found this

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by warfacegod on 2010-06-21
Thanks. This one worked for me in 9.10:```
sudo sh -c "sync; echo 3 > /proc/sys/vm/drop_caches"
```

---

