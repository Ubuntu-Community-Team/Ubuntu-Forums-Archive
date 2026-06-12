---
title: "Installed app with-out recommend packages, how to get them later ?"
date: 2009-10-26
forum: General Help
---

### Post by iMisspell on 2009-10-26
If you install a package with:
```
sudo aptitude --without-recommends install appname
```

Receive the following message:
"*The following packages are RECOMMENDED but will NOT be installed:*"
and continue with the install, how can you go back and install those recommend packages ?

I tried the following but neather worked.
```
sudo aptitude --with-recommends install appname
sudo aptitude reinstall appname
```

Being im just doing some testing - so to remove the app and reinstalled it again is not a big deal, but im looking to see if there is a command or flag which can run against the said appname and have it install the  recommend packages which where ignored the first time.
Note: im looking something for the command line.



_

---

### Post by ScarySquirrel on 2010-04-23
Short Answer: 
```
sudo apt-get --install-recommends
```

Short Haughty Answer:
```
man apt-get
```

---

