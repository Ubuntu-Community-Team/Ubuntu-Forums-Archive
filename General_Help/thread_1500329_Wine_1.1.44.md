---
title: "Wine 1.1.44"
date: 2010-06-03
forum: General Help
---

### Post by UnderPantGn0mes on 2010-06-03
cant install the new wine 1.1.44 it just gives me a folder that opens up to a lot more folders (im confused on how to get it to work)

---

### Post by Spr0k3t on 2010-06-03
How are you trying to install wine 1.1.44?  Are you using the PPA, installing from source?

For the PPA open a terminal and enter this:

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine
```

This should get you started in the right direction.  Granted it's not release 1.1.44 at this moment, but it will auto update when the PPA is updated.

---

