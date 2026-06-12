---
title: "apt-get Unmet dependencies problem"
date: 2010-03-11
forum: General Help
---

### Post by arahant on 2010-03-11
Hi,

I am trying to install the python-matplotlib package but I get E:broken packages.
I have tried the apt-get -f install, apt-get update, apt-get clean all in various permutations but it doesnt solve the problem.
I also tried uninstalling the dependednt packages and then reinstalling them but that doesnt work either. 

root@ubuntu:~# apt-get install python-matplotlib
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  python-matplotlib: Depends: libatk1.0-0 (>= 1.29.3) but 1.28.0-0ubuntu1 is to be installed
                     Depends: libfontconfig1 (>= 2.8.0) but 2.6.0-1ubuntu12 is to be installed
E: Broken packages

Here is what happens on apt-get -f install and apt-get clean all (same message for both)

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 193 not upgraded.

any help would be greatly appreciated.

---

### Post by gmargo on 2010-03-11
You are mixing and matching Lucid and Karmic packages, aren't you?  It's trying to install **python-matplotlib** from the Lucid repository.

---

### Post by arahant on 2010-03-12
You are right. 
I assume commenting out the karmic sources from sources.list and then installing all dependent packages from the lucid repositories should solve the problem? Is that right?

---

### Post by gmargo on 2010-03-12
> **arahant said:**
> You are right. 
I assume commenting out the karmic sources from sources.list and then installing all dependent packages from the lucid repositories should solve the problem? Is that right?
If your base system is Karmic, then that's a bad idea.  If you want to upgrade to Lucid early (only about 6 more weeks until official release) then do it properly (see [http://www.ubuntu.com/testing/lucid/alpha3](http://www.ubuntu.com/testing/lucid/alpha3).) Otherwise stick with Karmic for now.

---

