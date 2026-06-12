---
title: "Alien install fails 12.04"
date: 2012-08-08
forum: General Help
---

### Post by BruceFulton on 2012-08-08
Attempting to install Alien on 12.04 Server (32bit) in order to install some rpm packages, the installation fails with these two issues:

Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-libc-dev i386 3.2.0-26.41
  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main linux-libc-dev i386 3.2.0-26.41
  404  Not Found [IP: 91.189.92.184 80]
I checked the second one manually at the IP address listed and it does appear that it's missing. 

Suggestions?

---

### Post by BruceFulton on 2012-08-08
although very recently run, aptitude update resolved the problem.

---

