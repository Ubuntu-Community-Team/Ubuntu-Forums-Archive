---
title: "How-to validate &quot;dist&#8208;upgrade&quot; installation?"
date: 2011-03-11
forum: General Help
---

### Post by Maciej Miklas on 2011-03-11
Hi,

I would like to update to the newest distribution using dist&#8208;upgrade. 

Is there a way to validate if update was successfully? 

For example I would like to work few days with updated version and check few log files for possible errors. 
The question is what files should I check? Or maybe there is some better way....

Thanks,
Maciej

---

### Post by mcduck on 2011-03-11
> **Maciej Miklas said:**
> Hi,

I would like to update to the newest distribution using dist&#8208;upgrade. 

Is there a way to validate if update was successfully? 

For example I would like to work few days with updated version and check few log files for possible errors. 
The question is what files should I check? Or maybe there is some better way....

Thanks,
Maciej

While it's *possible* to upgrade to next release using dist-upgrade, simply running that command would not do the trick, you'd have to manually edit your sources.list to point to en version's repositories first. "apt-get dist-upgrade2 is just a slightly more powerful version of "apt-get upgrade", able to install new packages and remove installed once to resolve possibile conflicts.

Anyway, the recommended tools for a release upgrade are "*sudo do-release-upgrade*" (for command-line use) and "*gksudo update-manager -d*" (if you want a GUI tool)

Both tools will tell you if there were any errors during the upgrade.

---

### Post by lithopsian on 2011-03-11
dist-upgrade will tell you if it thinks packages are in an inconsistent state, but that doesn't necessarily mean your system will work.  It probably will be fine if you haven't done too much configuring away from the basic settings of the previous release.  I've dist-upgraded several times (only one release at a time!) and it has been fine except for one Jaunty->Karmic upgrade on a system that I'd customised quite a lot.

---

### Post by Maciej Miklas on 2011-03-11
I know that it should work... but the question is: can I verify it somehow?

I will search for errors in System Log - but this might be not enough....

---

