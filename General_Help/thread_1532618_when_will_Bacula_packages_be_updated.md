---
title: "when will Bacula packages be updated?"
date: 2010-07-16
forum: General Help
---

### Post by dreamgear on 2010-07-16
I'm building a new backup server, migrating from Centos to Ubuntu 10.04 LTS and upgrading to Bacula 5 all at the same time.

Is there a way to find out why there's a 3 month lag?  5.0.2 was released in April, and the currently available packages are 5.0.1.

Also how can I find the policy on future updates ?  I'd really like to use the core-provided packages but don't want to end up way behind after a year or two.

Thanks in advance.

---

### Post by clhsharky on 2010-07-16
dreamgear

Ubuntu is not a rolling release, thats why there is 2 releases a year. App's get upgraded to latest stable at feature freeze, not release date. This helps keep releases stable and fairly current.
Only bug fixes and security updates will be upgraded after release.
If you want a newer app install it from a deb or search for a ppa to keep you up to date. Servers should be stable, the latest greatest need to be tested before distros upgrade apps.

[http://www.ubuntuupdates.org/](http://www.ubuntuupdates.org/)

Apps do get updated for security reasons.

Sharky

---

### Post by dreamgear on 2010-07-18
Thanks.  My goal is to build a platform that will not need changes for long time, i.e. the "L" in LTS.  However, there were important bug fixes in Bacula 5.0.2.   I will have to find out what a "ppa" is.

---

### Post by Tidder on 2010-07-20
> **dreamgear said:**
> Thanks.  My goal is to build a platform that will not need changes for long time, i.e. the "L" in LTS.  However, there were important bug fixes in Bacula 5.0.2.   I will have to find out what a "ppa" is.

I don't believe there is a ppa with the newest version of Bacula.  You could try using the alien tool to convert the rpms on bacula's site to debs if you don't want to build from source.

With ubuntu LTS, "bleeding edge" isn't what they are going for.  As the previous poster said, they feature freeze, then get it to work as stable as it can be. You could possibly try using the deb packages from the debian lenny backports, but at that point I'd just use debian lenny.

---

