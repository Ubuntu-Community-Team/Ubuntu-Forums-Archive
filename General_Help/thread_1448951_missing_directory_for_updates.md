---
title: "missing directory for updates"
date: 2010-04-07
forum: General Help
---

### Post by TTTime on 2010-04-07
Sorry for being a newbee but i did something months ago that basically removed - i believe a directory that effected my update manager. Don't remember what i was playing with that did this but now no updates
this is what i get when i try to update - is there any way to re-create this directory please or fix this prob. any help appreciated


E: Could not open lock file /var/lib/apt/lists/lock - open (2 No such file or directory)
E: Unable to lock the list directory

---

### Post by sisco311 on 2010-04-07
Try to create the directory:
```
sudo mkdir -p /var/lib/apt/lists/partial
```
```
sudo apt-get update
```

---

