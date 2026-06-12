---
title: "My software center in not working!"
date: 2012-07-15
forum: General Help
---

### Post by LionsFootball on 2012-07-15
The Ubuntu software center stopped working. Here is the info it gives me:

Package operation failed:


nstallArchives() failed: dpkg: dependency problems prevent configuration of libmtp-dev:
 libmtp-dev depends on libmtp8 (= 1.0.2-1ubuntu1); however:
  Package libmtp8 is not installed.
dpkg: error processing libmtp-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing:
 libmtp-dev
Error in function: 
dpkg: dependency problems prevent configuration of libmtp-dev:
 libmtp-dev depends on libmtp8 (= 1.0.2-1ubuntu1); however:
  Package libmtp8 is not installed.
dpkg: error processing libmtp-dev (--configure):
 dependency problems - leaving unconfigured


Any help would be great, Thank you!

---

### Post by irv on 2012-07-15
Go to the package manager check for broken packages.
Clean them up and re-install the Software Center.

---

