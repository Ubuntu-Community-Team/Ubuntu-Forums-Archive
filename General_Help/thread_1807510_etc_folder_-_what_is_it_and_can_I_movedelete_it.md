---
title: "etc folder - what is it and can I move/delete it?"
date: 2011-07-19
forum: General Help
---

### Post by Mellifluous on 2011-07-19
New Ubuntu user here. After I installed it I have a folder on my desktop called 'etc'. It contains two other folders, 'pki' and 'yum.repos.d'. I have no idea what it's for. It's just hovering there on my desktop taking up space. What is it and can I move it or delete it without causing any problems?

---

### Post by Grenage on 2011-07-19
Yum isn't something Ubuntu uses, so I have no idea why that's there.  You should be able to remove it without incident.

---

### Post by mikejonesey on 2011-07-19
you could use yum but it's best to use one package manager or the other or your sys gets boop... on dependancies and will use different versions of so libs, (u'll end up with lots of c errors), yum was dev by yella dog linux to manage rpm (red hat package manager)... debian based systems use apt-get instead of yum which managed the deb package manager...

recomends: uninstall yum and rpm and all packages installed with yum, install with apt-get... only time you'll want rpm installed is to alien packages to deb format... (you should hardly ever need to do this... packages are ported over and in the deb repos in no time...)

---

### Post by SoFl W on 2011-07-19
You are not running a different distro and sharing a home drive are you?

---

### Post by Mellifluous on 2011-07-19
> **mikejonesey said:**
> recomends: uninstall yum and rpm and all packages installed with yum, install with apt-get... only time you'll want rpm installed is to alien packages to deb format... (you should hardly ever need to do this... packages are ported over and in the deb repos in no time...)

How do uninstall it? And how do I find out which packages have been installed with it? I'm a new user so go easy on the explanations, it's all gobbledegook to me at the moment :D

> **SoFl W said:**
> You are not running a different distro and sharing a home drive are you?

I have a Windows machine with Ubuntu installed with Wubi direct from the Ubuntu website. This is the only version of Linux I have.

---

