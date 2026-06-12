---
title: "problem with Ubuntu Tweak"
date: 2010-08-02
forum: General Help
---

### Post by Kmob810 on 2010-08-02
Until a couple of days ago I was able to use the excellent Ubuntu Tweak programme but all of a sudden I have found that I cannot 'unlock' the Package Cleaner. I Can't clean the packages or the cache or anything else.
Can anyone help with this?
I'm using 10.04
:p

---

### Post by panopticon on 2010-08-02
First guess is that there is no packages/cache to clean. Another thing is; what gives you an indication that you "can't" use the clean feature? Any error messages? Are you asked for your password?

---

### Post by Kmob810 on 2010-08-03
when I click on 'clean packages' for an example, then 'unlock' nothing happens, the unlock doesn't work. I don't get any messages and therefore I can't 'clean' anything. Everything worked great a few days ago.

---

### Post by panopticon on 2010-08-03
Try this. Alt + F2 and run: gksu ubuntu-tweak

See if that will allow you to apply the features you're requesting.

---

### Post by dcstar on 2010-08-03
> **Kmob810 said:**
> Until a couple of days ago I was able to use the excellent Ubuntu Tweak programme but all of a sudden I have found that I cannot 'unlock' the Package Cleaner. I Can't clean the packages or the cache or anything else.
Can anyone help with this?
I'm using 10.04
:p

That package was updated a few days ago, make a bug report.

---

### Post by Kmob810 on 2010-08-03
Brilliant    gksu ubuntu-tweak  worked a treat
Thanks everyone for all your help

---

