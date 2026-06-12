---
title: "Clean dpkg &quot;deinstall&quot; packages"
date: 2012-06-13
forum: General Help
---

### Post by Sergius14 on 2012-06-13
Hello,

I used to allways remove old kernels and packages with apt-get remove or autoremove/autoclean.

Now I want to clean the dpkg lists since there are growing with these old packages.

Seams that if I have uninstalled with purge instead of remove it would be it done but now I have the packages removed and I have to clean this list.

Example:

> linux-image-2.6.32-28-server                    deinstallHow can fully remove this without reinstall anything?


I have previusly done ```
apt-get remove linux-image-2.6.32-28-server
```

---

### Post by Sergius14 on 2012-06-13
I have done with this:

[http://nialldonegan.me/2007/09/05/cleaning-up-after-aptget-remove/](http://nialldonegan.me/2007/09/05/cleaning-up-after-aptget-remove/)



dpkg --purge `dpkg --get-selections | grep deinstall | cut -f1`

---

