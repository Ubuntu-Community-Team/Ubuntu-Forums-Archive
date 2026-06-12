---
title: "How can i uninstall Ubuntu-restricted-Extras?"
date: 2010-08-23
forum: General Help
---

### Post by Lukasz Tarkowski on 2010-08-23
How can i uninstall Ubuntu-restricted-Extras? Is there an dpkg option?  I would like to remove it and install it again

---

### Post by spcwingo on 2010-08-23
That package is a meta-package meaning it's just a package that has no content just a bunch of dependencies.  Sorry for the crude explanation...at least that's the way that I look at it.  To answer your question open synaptic and search for ubuntu-restricted-extras.  Then right-click the package and select "properties".  In the new window select the "dependencies" tab and make a note of all the packages listed.  After that either select all those packages from within synaptic or alternately, you could do it from the terminal with:

```
sudo apt-get install --reinstall "package names"
```

Of course replacing "package names" with the actual package names.

BTW,  I very seriously doubt that it will work, but you can try:

```
sudo apt-get install --reinstall ubuntu-restricted-extras
```

---

### Post by tal32123 on 2010-08-23
just use the software center

---

### Post by Lukasz Tarkowski on 2010-08-24
Thank you all, Amarok for kde  has messed up the Ubuntu system on my laptop, so I just reinstall entire Ubuntu

---

