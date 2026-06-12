---
title: "add yourself to the &quot;lp&quot; group"
date: 2012-02-20
forum: General Help
---

### Post by dockalek on 2012-02-20
Hi,
I need to know how to do this: "add yourself to the "lp" group".

I had problems with installing samsung printer driver, this [http://ubuntuforums.org/showthread.php?t=341621](http://ubuntuforums.org/showthread.php?t=341621) helped me a big deal, but I still have problems with connecting to scanner. In those instructions it tells to add user to lp group. I don't know how.
Thank you.

---

### Post by jocko on 2012-02-20
Open up a terminal and type this:
```
sudo adduser $USER lp
```
That'll do it.

---

