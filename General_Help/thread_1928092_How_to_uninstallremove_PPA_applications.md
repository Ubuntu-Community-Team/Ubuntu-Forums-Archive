---
title: "How to uninstall/remove PPA applications"
date: 2012-02-19
forum: General Help
---

### Post by Rebelli0us on 2012-02-19
These apps are shown in Update Manager > Settings > Other Software. I assume that if you uncheck it, it will stop updating. But how do you uninstall it?

For example I installed "VideoLAN Movie Creator" as per instructions here:

[http://trac.videolan.org/vlmc/wiki/Downloads](http://trac.videolan.org/vlmc/wiki/Downloads)

Installation worked fine but how do I get rid of the app?

---

### Post by oldos2er on 2012-02-19
```
sudo apt-get remove vlmc
``` or ```
sudo apt-get purge vlmc
``` if you want to remove its configuration files too.

---

### Post by bluexrider on 2012-02-19
follow oldos2er

then remove PPA
```

sudo ppa-purge ppa: rohityadav/vlmc
```

---

### Post by Rebelli0us on 2012-02-19
Thank you. Now if somebody searches Forums -- Topic Title for "uninstall PPA" there will be at least one hit.:popcorn:

---

