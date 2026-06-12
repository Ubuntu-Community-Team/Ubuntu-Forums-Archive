---
title: "Synaptic Package manager not starting"
date: 2009-12-30
forum: General Help
---

### Post by Dunchillin on 2009-12-30
Hi all,
I am trying to open synaptic package manager and keep getting an error message as follows popping up before it can open:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried typing what it said (dpkg --configure -a) into terminal but was informed that the "requested operation requires superuser privilege".  It doesn't ask for my password or anything else.

Have also tried restarting the computer and also to simply add a program from the applications list - same error message as synaptic.

Any ideas?  Thanks!

---

### Post by MelDJ on 2009-12-30
type 
sudo dpkg --configure -a

---

### Post by Dunchillin on 2009-12-30
Thank you! Always forget bloody sudo... ;)

---

