---
title: "Problems Uninstalling program, not shown on Synaptic"
date: 2011-05-13
forum: General Help
---

### Post by jezzyjez on 2011-05-13
I am running 11.04 and am trying to upgrade my VBox, when trying to uninstall i am having problems.It doesn't show as installed in Synaptic and when trying apt-get remove tabbing 'V' doesn't bring up virtualbox

The file was installed from the Virtualbox website I think it was a DEB file

Any ideas?

Thanks 
Jez

---

### Post by TeoBigusGeekus on 2011-05-13
Try with this
```
sudo dpkg --purge $(dpkg -l|grep -i virtualbox)
```

---

### Post by jezzyjez on 2011-05-15
> **TeoBigusGeekus said:**
> Try with this
```
sudo dpkg --purge $(dpkg -l|grep -i virtualbox)
```

This gave the error
```
dpkg: error: --purge needs at least one package name argument

```

---

