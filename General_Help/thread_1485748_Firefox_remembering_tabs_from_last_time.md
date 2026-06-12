---
title: "Firefox remembering tabs from last time"
date: 2010-05-17
forum: General Help
---

### Post by alan4cult on 2010-05-17
Hi, not sure is this a firefox problem or a problem with Ubuntu.
Whenever I log into firefox it remebers my tabs from last time and opens them again.
In Firefox preference I have set it not to remember the tabs so I think it maybe something to do with Ubuntu.
I'm running 10.04

Help appreciated?

---

### Post by lovinglinux on 2010-05-17
Type **about[noparse]:[/noparse]config** in the address bar, then type **browser.startup.page** in the filter and check if that preference value is not **3**. Change it to **0** to open a blank page and **1** to open your home page.

If the preference is not 3 already, then go to your Firefox profile folder (.i.e ~/.mozilla/firefox/<profile>) and delete the file **sessionstore.js**.

If that doesn't work, then see [http://kb.mozillazine.org/Session_Restore](http://kb.mozillazine.org/Session_Restore)

---

