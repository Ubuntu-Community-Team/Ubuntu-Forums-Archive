---
title: "Synaptic stops responding when trying to clear cache of deb install packages"
date: 2010-11-30
forum: General Help
---

### Post by nmyrick on 2010-11-30
My synaptic stops responding when I try to clear cache of old deb install packages.  Can anyone help me with this?

---

### Post by plucky on 2010-11-30
> **nmyrick said:**
> My synaptic stops responding when I try to clear cache of old deb install packages.  Can anyone help me with this?

Open a terminal and ```
sudo apt-get clean
sudo apt-get autoremove
```

This will clear out all the installed .deb packages in var/cache/apt/archives and remove packages that were automatically installed to satisfy dependencies.


Good Luck

---

### Post by nmyrick on 2010-11-30
I don't want to remove packages that were installed to satisfy dependencies, since Ubuntu computer janitor has a bad habit of removing things that are still needed by software that did not originally come with the OS.  I just want to remove the old .deb packages.  Is that just the sudo apt-get clean?

---

### Post by plucky on 2010-11-30
> **nmyrick said:**
> I don't want to remove packages that were installed to satisfy dependencies, since Ubuntu computer janitor has a bad habit of removing things that are still needed by software that did not originally come with the OS.  I just want to remove the old .deb packages.  Is that just the sudo apt-get clean?

Yes

---

