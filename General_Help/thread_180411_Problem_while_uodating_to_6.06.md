---
title: "Problem while uodating to 6.06"
date: 2006-05-22
forum: General Help
---

### Post by october1917 on 2006-05-22
I try to update my Ubuntu 5.10 to 6.06 but there is a problem. While i wahe allready done the 2 first steps of updating, "...", "changing repositories", in the third part "downloading and installing updates" after having downloading all the 36 packs it starts "checking package manager". then stops and a window appears writtingQ:

> Could not calculate the upgrade
A unresolvable problem occured while calculating the upgrade. Please report this as a bug.

There is only one report of this problem here "https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/41023" but i cannot understand the way to resolve it. Is it resolvable? Are there some setup in the existing version in my pc in order to accept the new update? What do i have to do?

Thank you

---

### Post by miceagol on 2006-06-09
I have the exact same problem... Could somebody answer this? 

I get no error messages in the terminal when this error window pops up, but this was my output when the update program was running:
```

michaeka@laptop:~$ gksudo "update-manager"
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
/usr/lib/python2.4/site-packages/UpdateManager/MetaRelease.py:171: DeprecationWarning: Class MetaRelease is already GObject-registered; Please note that classes containing any of the attributes __gtype_name__, __gproperties__, or __gsignals__ are now automatically registered.
  gobject.type_register(MetaRelease)
extracting '/tmp/tmpbhfOXT/dapper.tar.gz'
authenticate '/tmp/tmpbhfOXT/dapper.tar.gz' against '/tmp/tmpbhfOXT/dapper.tar.gz.gpg'
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

```

---

### Post by miceagol on 2006-06-10
Well, I figured I'd try the "Upgrading by changing sources and the command line" instead, and it worked. This should be the solution for people out there with this error message.

Please follow the instruction on [https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades) carefully. I experienced some slight problems I solved before I completed the upgrade, so just ask if you need help. :)

---

### Post by Griffongob on 2006-12-27
wait explain how u did thst I have the same problem

---

