---
title: "reinstall screen"
date: 2011-06-29
forum: General Help
---

### Post by goltoof on 2011-06-29
how do I reinstall screen?

---

### Post by goltoof on 2011-06-29
> **goltoof said:**
> how do I reinstall screen?

I should clarify.. I uninstalled php5 the wrong way and it proceeded to uninstall all php dependencies.  Reinstalled php5. It shows screen is still installed but can't get it to run. Tried removing/installing and I get:

```
/var/run/screen/$-lee/3305.pts-0:  No such file or directory
```

---

### Post by Habitual on 2011-06-29
open a terminal and 
```
sudo kill 3305
sudo dpkg --purge screen
sudo apt-get install screen

```

---

