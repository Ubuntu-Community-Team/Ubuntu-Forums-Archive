---
title: "Cups printing breaks after applying updates.  Ubuntu 10.4"
date: 2010-07-22
forum: General Help
---

### Post by mutineer612 on 2010-07-22
I noticed that after applying updates to my ubuntu 10.4 desktop my printer was not working.  I discovered that cups was no longer running and I was unable to get it to start.  

After re-installing cups using the below command everything is now working.  This is the 2nd time I've had to re-install cups after patching.  

> sudo apt-get install --reinstall cups

This appears to be a critical bug: [#554172]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554172")

---

### Post by AlphaLexman on 2010-07-22
Can you connect to:
```
http://localhost:631
```in a browser?

Edit: Love your avatar!

---

### Post by mutineer612 on 2010-10-11
This issue was solved with a recent kernel update.

---

