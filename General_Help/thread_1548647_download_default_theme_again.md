---
title: "download default theme again"
date: 2010-08-08
forum: General Help
---

### Post by ricardino on 2010-08-08
hi all,

ive foolishly installed the ambiance beta themes from the murrine ppa, however im not keen on the result. However, during installation, they deleted the default ambiance and radiance and themes. What i want to know is which package do i need to install to get my default themes back?

Any help would be appreciated

---

### Post by chopinhauer on 2010-08-08
> **ricardino said:**
> 
ive foolishly installed the ambiance beta themes from the murrine ppa, however im not keen on the result. However, during installation, they deleted the default ambiance and radiance and themes. What i want to know is which package do i need to install to get my default themes back?


The themes are in the **light-themes** package. A
```
sudo apt-get install --reinstall light-themes/lucid
```
should reinstall it. Otherwise deactivate the PPA and try again.

---

