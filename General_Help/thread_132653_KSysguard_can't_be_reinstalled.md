---
title: "KSysguard can't be reinstalled"
date: 2006-02-18
forum: General Help
---

### Post by gnutux on 2006-02-18
Hey all, I just came back to Kubuntu after experiencing hell with PCBSD. Yet, after upgrading KDE to 3.5.1, I lost ksysguard and tried reinstalling it. >  Reading package lists... Done Building dependency tree... Done Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming. Since you only requested a single operation it is extremely likely that the package is simply not installable and a bug report against that package should be filed. The following information may help to resolve the situation: The following packages have unmet dependencies: ksysguard: Depends: kdelibs4c2 (>= 4:3.4.3-1) but 4:3.4.3-0ubuntu1 is to be installed E: Broken packages  

I need my KSysguard back :(

gnutux

---

### Post by Lord Illidan on 2006-02-18
Try a ```
sudo apt-get -f install 
``` but post output here before entering Y/N

---

### Post by gnutux on 2006-02-18
> 
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  kdelibs-bin kdelibs4c2 libavahi-client1 libavahi-common0 libavahi-qt3-0
Recommended packages:
  avahi-daemon
The following NEW packages will be installed:
  ksysguard libavahi-client1 libavahi-common0 libavahi-qt3-0
The following packages will be upgraded:
  kdelibs-bin kdelibs4c2
2 upgraded, 4 newly installed, 0 to remove and 74 not upgraded.
Need to get 9828kB of archives.
After unpacking 2593kB of additional disk space will be used.
Do you want to continue [Y/n]?


Here it is

gnutux

---

### Post by gnutux on 2006-02-19
Nevermind, I solved it.

gnutux

---

