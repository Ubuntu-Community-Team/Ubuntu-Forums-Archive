---
title: "Can't get gpg key"
date: 2009-08-13
forum: General Help
---

### Post by Hawk__0 on 2009-08-13
I'm trying to install chromium and whenever I try to install the key it just hangs:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xfbef0d696de1c72ba5a835fe5a9bf3bb4e5e17b5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 0xfbef0d696de1c72ba5a835fe5a9bf3bb4e5e17b5
gpg: requesting key 4E5E17B5 from hkp server keyserver.ubuntu.com
<hangs here>

fixed, wrong version listed in sources

---

### Post by michy99 on 2009-08-13
Are you sure you have the right key? That string looks awfully long. Where did you get it from?

EDIT: Never mind, I see you fixed it.

---

