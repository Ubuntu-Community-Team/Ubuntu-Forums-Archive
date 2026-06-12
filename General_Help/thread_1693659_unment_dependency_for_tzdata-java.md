---
title: "unment dependency for tzdata-java"
date: 2011-02-23
forum: General Help
---

### Post by cannonfodder on 2011-02-23
Encountering problems while trying to install Frostwire 4.21.3 on a day-old install of Ubuntu 10.10 (Mavreick). All files are up to date as of yesterday.

The sun-java6-bin install went well, i.e., no error messages. 

However, when I use gdebi to install the deb I downloaded from the Frostwire site (frostwire-4.21.3.all.deb), I get "Error: Cannot install 'default-jre-headless'".

If I try to install default-jre-headless, I get:


The following packages have unmet dependencies:
  tzdata-java: Depends: tzdata (= 2010l-1) but 2010o-0ubuntu0.10.10 is installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     default-jre-headless [Not Installed]               
2)     icedtea-6-jre-cacao [Not Installed]                
3)     openjdk-6-jre-headless [Not Installed]             
4)     openjdk-6-jre-lib [Not Installed]                  
5)     tzdata-java [Not Installed]                        



Accept this solution? [Y/n/q/?] 

At this point, no matter what option I select (default, 1, r 1, etc.) nothing gets installed.

Thanks in advance

---

### Post by gmargo on 2011-02-23
This is semi-baffling because both the **tzdata-java** and **tzdata** packages should have the exact same version number.

> 
The following packages have unmet dependencies:
  tzdata-java: Depends: tzdata (= 2010l-1) but 2010o-0ubuntu0.10.10 is installed.
The current version of **tzdata-java** is 2010o-0ubuntu0.10.10, which depends on **tzdata** also version 2010o-0ubuntu0.10.10.  You seem to be trying to install the old version of **tzdata-java** (2010l-1), which which depends on **tzdata** (2010l-1) while the new version of **tzdata** (2010o-0ubuntu0.10.10) is already installed.  Since they both come from the **maverick-updates** repository, I don't see how this could be. You're not trying to install software from the CDROM, are you?

I suggest making sure that all of the repositories are enabled and running
```

aptitude update
aptitude full-upgrade

```and then try again.

---

### Post by ectospasm on 2011-03-15
I've tried this, but still tzdata-java is depending on the old tzdata version (2010l-1).  Seems like an upgrade went nuts, or at least the current version of tzdata-java depends on the old version of tzdata.

I will check launchpad and report back.

---

### Post by ectospasm on 2011-03-15
I searched [http://launchpad.net](http://launchpad.net) (bug tracker for official Ubuntu releases), and saw that there were new versions of tzdata and tzdata-java available (version 2011c-0ubuntu0.10.10).  I downloaded the latest "proposed" releases, and installed them with dpkg (actual output removed for brevity):

```
~ # wget http://launchpadlibrarian.net/65852669/tzdata_2011c-0ubuntu0.10.10_all.deb 
~ # dpkg -i tzdata_2011c-0ubuntu0.10.10_all.deb 
~ # wget http://launchpadlibrarian.net/65852670/tzdata-java_2011c-0ubuntu0.10.10_all.deb
~ # dpkg -i tzdata-java_2011c-0ubuntu0.10.10_all.deb 
~ # aptitude -y install default-jre

```

These (at least) let me install a JRE, so now LibreOffice will hopefully work.  Yep, LibreOffice no longer complains in a loop!

---

