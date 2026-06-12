---
title: "update manager"
date: 2010-07-27
forum: General Help
---

### Post by gregpo on 2010-07-27
update manager installed 75 files on my ubuntu 10.4 took  4 hours did i really need them& how do I find & decrypt  what they are to late now, but for future installs interested in learning about ubuntu in lieu of windows & joined a club called "humbug" but after a few months found them to be very esoteric whats the big secret?

---

### Post by drs305 on 2010-07-27
You can open Update Manager and click on the Settings box. Go to the Updates tab. Make sure you have the "Important security updates" checked. Normally the "Recommended Updates" is also a good thing to have checked but if your system is working fine and you don't want updates you don't really need these. They are recommended because they often contain fixes to packages you have installed on your system. 

With rare exceptions, Ubuntu doesn't upgrade packages to newer versions (Firefox 3 to Firefox 4, for instance) within a release, so getting the updates is usually a good idea.

You certainly don't need the "proposed" or "unsupported backports" repositories from the Update tab unless you have a specific need for them. Even then, unless you have a reason, it's best it activate the repository, get what you need, and then deselect it again if there is a specific package you want.

As far as seeing what you download, you can set the option in the same tab as to how often you get updates and whether you want to see them first. You can expand the "Description" in the lower left part of the Update Manager to see the changelog notes, if supplied, for each app.

As far as what was recently installed on your system, on recent versions of Ubuntu you can go to System, Administration, Log File viewer and look at the dpkg.log to see the files recently installed. For a simpler view, you could run this command to see what was recently installed:
```
cat /var/log/dpkg.log | grep "status installed"
```

---

### Post by 3rdalbum on 2010-07-27
> **gregpo said:**
> update manager installed 75 files on my ubuntu 10.4 took  4 hours did i really need them

If they were listed under "Important Security Updates", then they were important. If they were listed under "Recommended Updates", then they were recommended :-)

> how do I find & decrypt  what they are to late now, but for future installs

For each package that appears in Update Manager, you can click it and click the "Changelog" tab to retrieve a list of changes in this package. Some of it you won't understand, some of it you might (for instance "Fixed crash on logout"). But basically, if it's a security update or "recommended", then you really should have it.

---

### Post by gregpo on 2010-07-27
have just opened UM and recomended updates for empathy which i don/t use willi uncheck box/s to cancel

---

