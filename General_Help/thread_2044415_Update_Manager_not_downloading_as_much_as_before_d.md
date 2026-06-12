---
title: "Update Manager not downloading as much as before during update check"
date: 2012-08-19
forum: General Help
---

### Post by james_mcl on 2012-08-19
System - Administration - Update Manager.

Press "Check".

Now, until recently, the update check (which I did once per day) downloaded about 15MB of data checking for updates. Suddenly, this has dropped substantially, seeming to vary in the last week or so between one byte and 1.XMB.

Although this is good news for the time taken to check (and for my bandwidth usage!) it does seem rather odd. Has anyone else noticed that update checks (in particular on Natty) are suddenly downloading less information?

---

### Post by raja.genupula on 2012-08-19
actually its matter about the changes in the sources . actually when did update first of all the sources cache information will be update .
if No changes are done on some sources then No need to update the cache information of that source else if any changes then should a update of cache information .

so the size depends on  the changes of your sources cache information ,:)

---

### Post by plucky on 2012-08-19
> **james_mcl said:**
> System - Administration - Update Manager.

Press "Check".

Now, until recently, the update check (which I did once per day) downloaded about 15MB of data checking for updates. Suddenly, this has dropped substantially, seeming to vary in the last week or so between one byte and 1.XMB.

Although this is good news for the time taken to check (and for my bandwidth usage!) it does seem rather odd. Has anyone else noticed that update checks (in particular on Natty) are suddenly downloading less information?

This might help [Bug Report](https://bugs.launchpad.net/ubuntu/+bug/1001780)

Good Luck

---

### Post by james_mcl on 2012-08-27
Thanks Plucky - that looks like the reason.

---

