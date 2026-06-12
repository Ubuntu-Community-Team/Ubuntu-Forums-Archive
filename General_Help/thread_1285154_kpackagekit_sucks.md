---
title: "kpackagekit sucks"
date: 2009-10-07
forum: General Help
---

### Post by skakid177 on 2009-10-07
kpackagekit in karmic wont let me install any packages it says i dont have privliges to do so, and i do.  :confused:

---

### Post by kellemes on 2009-10-07
> **skakid177 said:**
> kpackagekit in karmic wont let me install any packages it says i dont have privliges to do so, and i do.  :confused:

Your title sucks too.. you won't get a lot of help with this negative attitude.

Your issue seems to be related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/policykit-kde/+bug/353278") and may be resolved like so..
```
sudo apt-get install policykit
```

---

