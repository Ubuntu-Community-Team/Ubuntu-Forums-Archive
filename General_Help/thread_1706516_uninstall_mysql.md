---
title: "uninstall mysql?"
date: 2011-03-14
forum: General Help
---

### Post by Adrienk on 2011-03-14
how would i do it through terminal so that EVERY thing got unistalled?

---

### Post by lithopsian on 2011-03-14
Not sure what you mean by every thing?

To uninstall mysql and its configuration files and any library packages only needed by mysql:
```

sudo apt-get purge mysql-server-5.0
sudo apt-get --purge autoremove

```

You can also do dpkg -l to see if you still have any mysql packages left and then do the same for them.  Any mysql databases that you have created will still be on your system.

---

