---
title: "Error setting up checkbox-gtk"
date: 2010-06-06
forum: General Help
---

### Post by Gu3r0_9 on 2010-06-06
I haven't been able to install any programs recently in Lucid. I thought it was related to another error message I would get while updating but I resolved that problem but I still run into the same error in every install.

When I run the following

```
dpk --configure -a
```

I get

```
Setting up checkbox-gtk (0.9.1) ...
Compiling /usr/lib/python2.6/dist-packages/checkbox_gtk/gtk_interface.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
pycentral: pycentral pkginstall: error byte-compiling files (3)
pycentral pkginstall: error byte-compiling files (3)
dpkg: error processing checkbox-gtk (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on checkbox-gtk; however:
  Package checkbox-gtk is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hwtest-gtk:
 hwtest-gtk depends on checkbox-gtk; however:
  Package checkbox-gtk is not configured yet.
dpkg: error processing hwtest-gtk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 checkbox-gtk
 ubuntu-desktop
 hwtest-gtk
```

Any ideas?

---

### Post by lavinog on 2010-06-07
start with:
```

sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by Gu3r0_9 on 2010-06-07
That gives me the same output as dpkg

---

### Post by Coplen on 2011-04-07
Go into /var/lib/dpkg/info and delete everything that had the name of the messed up package. If checkbox is screwy - cd to that directory I mentioned and then rm check*

:D

---

