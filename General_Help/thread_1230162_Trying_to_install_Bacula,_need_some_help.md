---
title: "Trying to install Bacula, need some help"
date: 2009-08-03
forum: General Help
---

### Post by sincityharley on 2009-08-03
I installed everything via synaptic. When starting the Bacula Admin Tool I get 20 errors all saying 

 p, li { white-space: pre-wrap; }  02-Aug 23:11 bacula-server-dir: ERROR in authenticate.c:380 Unable to authenticate console "localhost-mon" at client:127.0.0.1:36131


Would anyone be able to assist with some troubleshooting?

---

### Post by sincityharley on 2009-08-03
bump

---

### Post by smylie on 2009-08-03
> **sincityharley said:**
> I installed everything via synaptic. When starting the Bacula Admin Tool I get 20 errors all saying 

 p, li { white-space: pre-wrap; }  02-Aug 23:11 bacula-server-dir: ERROR in authenticate.c:380 Unable to authenticate console "localhost-mon" at client:127.0.0.1:36131


Would anyone be able to assist with some troubleshooting?

Check the client and server configuration files to make sure all the passwords are correct, and the names of the allowed directories are correct.

Dave

---

