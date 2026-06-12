---
title: "How to check for latest security updates from terminal?"
date: 2010-03-03
forum: General Help
---

### Post by karthick87 on 2010-03-03
Is it possible to get security updates alone using terminal?If so how?

---

### Post by Swagman on 2010-03-03
```
sudo apt-get update
```

then

```
sudo apt-get upgrade
```

---

### Post by bashphoenux on 2010-03-03
```
 sudo apt-get update
```

---

### Post by karthick87 on 2010-03-03
> **bashphoenux said:**
> ```
 sudo apt-get update
```

It upgrades the whole system right?I need only security updates..

---

### Post by mcduck on 2010-03-03
There's no such option, just like none of the other ways to check for updates have any options to only *check* for security update (you can of course select which updates you *install* with Synaptic/Update manager.)

If you really want to only install the security, but disabling other than the security repository is out of the question, you might be able to do that with Aptitude or by selecting the packages to upgrade with dselect and then doing a "apt-get dselect-upgrade".. I don't think apt-get itself has any options for such things as it doesn't really make much sense (if you have others than just security repository enabled it can be quite safely assumed that you'd also want to use those repositories.) Besides, all the updates you'll get in Ubuntu are either security updates or bug fixes, so it really makes sense to install them all.

(so, the short answer is to disable all the other repositories than security.ubuntu.com)

---

### Post by QLee on 2010-03-03
> **getyourkarthick said:**
> Is it possible to get security updates alone using terminal?If so how?

If you are using a released version, available updates are not feature updates, they are security updates and bug fixes, ...and, chances are, you want them.

---

