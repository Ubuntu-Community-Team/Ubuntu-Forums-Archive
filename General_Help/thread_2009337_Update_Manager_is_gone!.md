---
title: "Update Manager is gone!"
date: 2012-06-24
forum: General Help
---

### Post by billcauley on 2012-06-24
After an update on Thursday, I've sequentially lost all of Libreoffice, and now the Update Manager won't load.  Message says: "It seems that the daemon died."

What should I do??

---

### Post by Enigmapond on 2012-06-24
Try un-installing the update manager and then re-installing.

```
sudo apt-get purge update-manager && sudo apt-get install update-manager
```

---

### Post by billcauley on 2012-06-24
> **Enigmapond said:**
> Try un-installing the update manager and then re-installing.

```
sudo apt-get purge update-manager && sudo apt-get install update-manager
```

Nope!  Didn't work.  Don't have synaptic either.

---

