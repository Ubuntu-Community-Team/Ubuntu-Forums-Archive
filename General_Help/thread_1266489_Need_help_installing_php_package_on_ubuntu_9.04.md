---
title: "Need help installing php package on ubuntu 9.04"
date: 2009-09-14
forum: General Help
---

### Post by xZachtmx on 2009-09-14
Ok im trying to get php5 for my computer.  So i typed in [I]sudo apt-get install php5 libapache2-mod-php5 but i got this error when it was trying to download:

[/I]```
Err http://ca.archive.ubuntu.com jaunty-updates/main php5-common 5.2.6.dfsg.1-3ubuntu4.1
  404 Not Found [IP: 91.189.88.140 80]
Err http://security.ubuntu.com jaunty-security/main php5-common 5.2.6.dfsg.1-3ubuntu4.1
  404 Not Found
Err http://security.ubuntu.com jaunty-security/main libapache2-mod-php5 5.2.6.dfsg.1-3ubuntu4.1
  404 Not Found
Err http://security.ubuntu.com jaunty-security/main php5 5.2.6.dfsg.1-3ubuntu4.1
  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5.2.6.dfsg.1-3ubuntu4.1_i386.deb 404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.2.6.dfsg.1-3ubuntu4.1_i386.deb 404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5_5.2.6.dfsg.1-3ubuntu4.1_all.deb 404 Not Found
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.

```


Does anyone know what this might mean?

---

### Post by KiLaHuRtZ on 2009-09-14
Have you updated your repositories?

```
sudo apt-get update
```

Also, you can just install 'php5' and the dependencies will auto-magically be installed as well. :)

---

### Post by xZachtmx on 2009-09-15
Wow! youre awesome thanks i just had to do the update thing you said
:P:P

---

### Post by KiLaHuRtZ on 2009-09-15
No problem.  Glad it solved your issue.  Also, a good practice is to update the repositories before installing upgrades.

```
sudo apt-get update && sudo apt-get upgrade
```

---

