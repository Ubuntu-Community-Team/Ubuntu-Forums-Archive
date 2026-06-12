---
title: "clean up trash"
date: 2010-05-08
forum: General Help
---

### Post by altjx on 2010-05-08
i downloaded and installed k3b from the software center and remember seeing that after it was installed, an additional 180MB would be taken up. so the installation process took about 2-3 minutes after unpackaging or whatever it does...

but when i went to uninstall it, it took like 2 seconds. is there a way to clean up packages that hasn't been uninstalled all the way or haven't been used? is that normal?
hmm..

---

### Post by altjx on 2010-05-08
such a crowded forum nowadays... anyone have any idea how?

---

### Post by marshmallow1304 on 2010-05-08
The command
```
sudo apt-get autoremove
```
will remove packages that were installed as dependencies of other packages that are no longer installed.

---

### Post by altjx on 2010-05-08
> **marshmallow1304 said:**
> The command
```
sudo apt-get autoremove
```
will remove packages that were installed as dependencies of other packages that are no longer installed.

thanks

---

### Post by linuxman94 on 2010-05-08
Mark your thread as solved using the Thread Tools menu at the top of the thread.

---

