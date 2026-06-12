---
title: "linux images"
date: 2010-07-02
forum: General Help
---

### Post by behzadsh on 2010-07-02
hi,
I only have a little question.
what's the different between these

```

linux-image-2.6.xx-xx-386
linux-image-2.6.xx-xx-generic
linux-image-2.6.xx-xx-generic-pae
linux-image-2.6.xx-xx-virtual
...
and some other linux images.

```

One more question. is it necessary to remove older linux image while installing new version?

thanks ;)

---

### Post by dino99 on 2010-07-02
when you select a package into synaptic (package manager), you can set your prefs to view the package properties:

synaptic menu: config -> prefs -> general tab: check the first line (show the package properties in main window)

you will see the difference(s) between package(s) and meta-package(s)

if your computer is using more than 3 Gb on a i386 release (32 bits), you may want to install the "pae" kernel to fully use the ram (this is the best choice as 64 bits installation have more issues)

the meta-package take care for you for good installation and upgrading. Sometimes user can have an issue with an installed kernel, so its a good idea to have 2 (or more) installed kernel (each one put two choices into grub menu: the normal and the recovery choice)

more info with the links below

---

### Post by behzadsh on 2010-07-02
thanks dino99

---

