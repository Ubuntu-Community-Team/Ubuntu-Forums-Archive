---
title: "Cannot execute file RUN_SYBASE"
date: 2011-10-17
forum: General Help
---

### Post by Maximus1285 on 2011-10-17
Hello folks!!

I'm trying to install Sybase 15.5 on ubuntu 11.04

It's currently install, however when I go to /opt/sybase/ASE-15_0/install and try to run ./startserver
I get the following message:
Cannot execute file RUN_SYBASE 

I have already install libaio and configured kernel.shmmax = 30000000000

and it's still not working.... can anybody help me on this or give some advices... Thanks in advance

---

### Post by Maximus1285 on 2011-10-17
I just noticed that the file RUN_SYBASE doesn't even exist on my directory, but I don't know why though...

---

### Post by ubuntu-user on 2011-10-24
If the RUN_SYBASE_ASE file is not there it seems that installation is not complete. Check the log and see for ERRORS.

---

