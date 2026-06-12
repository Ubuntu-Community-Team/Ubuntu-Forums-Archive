---
title: "Crashes, Lower file is not in a valid eCryptfs format"
date: 2012-09-03
forum: General Help
---

### Post by mio1 on 2012-09-03
I have the same problem [as [http://ubuntuforums.org/showthread.php?t=1377625]](http://ubuntuforums.org/showthread.php?t=1377625]) with Ubuntu 12.04 on a Dell Precision M4500 with a new Samsung SSD (MZ-7PC512N/EU 512 GB). It was a fresh install of Ubuntu 12.04 on that SSD. I chose to have my home dir encrypted during the installation.

The crashes seem to follow no pattern and freeze the whole system. Typically the mouse pointer would stop responding and make one "final" jump on the screen after one or two seconds. After that, the system is completely frozen, and I have to switch the notebook off completely before it would restart.

My syslog is full of eCryptfs complaints like the following. They are generated all the time, not only just before the crash, so I don't know if they are related:

> Sep  3 11:35:10 nemec-Precision-M4500 kernel: [ 4094.407568] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
Sep  3 11:35:10 nemec-Precision-M4500 kernel: [ 4094.420449] Valid eCryptfs headers not found in file header region or xattr region, inode 15991005

---

### Post by oldos2er on 2012-09-03
Post moved to its own thread.

---

