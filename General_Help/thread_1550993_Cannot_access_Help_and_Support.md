---
title: "Cannot access Help and Support"
date: 2010-08-11
forum: General Help
---

### Post by TheWeakSleep on 2010-08-11
I don't necessarily NEED this, but when i open yelp nothing happens, when i run it through the terminal it outputs ```
Could not initialize gecko!
``` What is happening here?

---

### Post by TheWeakSleep on 2010-08-13
bump

---

### Post by drascus on 2010-08-18
I am having the same problem on my X64 machine...

---

### Post by drascus on 2010-08-18
Okay this relates to this bug: [https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9.2/+bug/568876](https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9.2/+bug/568876) I am going to try and upgrad xulrunner and see if it works.

---

### Post by drascus on 2010-08-19
Okay I fixed this for myself. I forgot but I had a ppa installed for mozilla that installed an update that broke my gecko. deleted the ppa uninstalled firefox. Then I cleaned my configuration files and apt ( i use bleachbit and ubuntu tweak for that). Then I went into synaptic and installed the default version of Firefox for ubuntu 10.04. after this my system has been fine. help now works and I don't get gecko errors anymore.

---

### Post by TheWeakSleep on 2010-08-22
Thank you for your help. Are you using the mozilla nightly ppa?

---

