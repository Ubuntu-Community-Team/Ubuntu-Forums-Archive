---
title: "Can't Install Chromium"
date: 2011-06-19
forum: General Help
---

### Post by benc1213 on 2011-06-19
Everytime I try to install Chromium via the software centre or the terminal I get this error:

The following packages have unmet dependencies:

chromium-browser: Depends: libgcc1 (>= 1:4.1.1) but 1:4.5.2-8ubuntu4 is to be installed
                  Depends: libxdamage1 (>= 1:1.1) but 1:1.1.3-1ubuntu1 is to be installed
                  Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu3 is to be installed
                  Depends: libnss3-1d (>= 3.12.3) but it is not going to be installed

---

### Post by nzjethro on 2011-06-19
Hi there, try the following commands

```
sudo apt-get -f install
sudo apt-get autoremove
sudo apt-get clean all
sudo apt-get update
```

Then try reinstall.

---

