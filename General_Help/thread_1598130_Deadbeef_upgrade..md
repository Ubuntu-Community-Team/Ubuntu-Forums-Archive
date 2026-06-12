---
title: "Deadbeef upgrade."
date: 2010-10-16
forum: General Help
---

### Post by kimme on 2010-10-16
I have an problem with installing this update.

deadbeef

installArchives() failed: dpkg: parse error, in file '/var/lib/dpkg/status' near line 17721 package 'python-gmenu':

 `instal|ed' is not allowed for third (status) word in `status' field

How to solve this problem?

---

### Post by plucky on 2010-10-16
> **kimme said:**
> I have an problem with installing this update.

deadbeef

installArchives() failed: dpkg: parse error, in file '/var/lib/dpkg/status' near line 17721 package 'python-gmenu':

 `instal|ed' is not allowed for third (status) word in `status' field

How to solve this problem?

```
gksudo gedit /var/lib/dpkg/status
```

Then use **Find** and look for **python-gmenu** and it should look like > Package: python-gmenu
Status: install ok installed
Priority: optional
Section: python
Installed-Size: 184
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Architecture: amd64


`instal|ed' is not allowed for third (status) word in `status' field

 In the status line should say **installed** not **instal|ed**.

Good Luck

---

### Post by kimme on 2010-10-16
Thanks, This made my update work. :)

---

