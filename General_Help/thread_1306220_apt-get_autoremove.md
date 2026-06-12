---
title: "apt-get autoremove"
date: 2009-10-30
forum: General Help
---

### Post by bwm71 on 2009-10-30
apt-get is telling me the following:

> The following packages were automatically installed and are no longer required:
  libboost-thread1.34.1 libboost-date-time1.34.1 procmail sensible-mda virtualbox-ose-source
Use 'apt-get autoremove' to remove them.


I understand that this is a dependency thing, but I definitely use procmail, so I don't want to "apt-get autoremove".  How do I get procmail out of this list?

---

### Post by HiImTye on 2009-10-30
```
sudo apt-get remove libboost-thread1.34.1 libboost-date-time1.34.1 sensible-mda virtualbox-ose-source
```

will remove them (just leave procmail out as I did)

---

### Post by bwm71 on 2009-10-30
Sure, I understand that.  "apt-get install procmail" is what I was looking for.  It sets the packaged to manually installed.

---

