---
title: "Error installing python-wxgtk2.8"
date: 2010-09-24
forum: General Help
---

### Post by acrocephalus on 2010-09-24
Hello,
I am trying to upgrade to python-wxgtk2.8 but I get this error:

```
E: python-changesettings: subprocess installed post-installation script returned error exit status 1
E: python-meminfo-total: subprocess installed post-installation script returned error exit status 1
E: python-wxgtk2.8: subprocess installed post-installation script returned error exit status 1
E: python-wxgtk2.8-dbg: dependency problems - leaving unconfigured
```

Can anyone help me to solve it?
Cheers!

Dani

---

### Post by acrocephalus on 2010-09-24
For some reason, there was no symbolic link pointing to the python version, so I run
```
sudo ln -s python<your-version-number> /usr/bin/python
```
and now it works like a charm.

Dani

---

