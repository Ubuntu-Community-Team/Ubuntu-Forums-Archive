---
title: "LibreOffice broke Openoffice, can't reinstall OO"
date: 2011-04-19
forum: General Help
---

### Post by Elvis99 on 2011-04-19
Hi Everybody,

I'm in a dire situation: Libreoffice broke the openoffice package, and now I am unable to reinstall openoffice both on a 10.04 and a 10.10 system: 

```

elvis@graceland:~$ sudo apt-get install openoffice.org

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 openoffice.org : Depends: openoffice.org-core (= 1:3.2.1-7ubuntu1) but it is not going to be installed
                  Depends: openoffice.org-writer but it is not going to be installed
                  Depends: openoffice.org-calc but it is not going to be installed
                  Depends: openoffice.org-impress but it is not going to be installed
                  Depends: openoffice.org-draw but it is not going to be installed
                  Depends: openoffice.org-math but it is not going to be installed
                  Depends: openoffice.org-base but it is not going to be installed
                  Depends: openoffice.org-report-builder-bin but it is not going to be installed
                  Depends: openoffice.org-officebean but it is not going to be installed
                  Depends: openoffice.org-filter-mobiledev but it is not going to be installed
                  Depends: openoffice.org-java-common (>= 1:3.2.1~) but it is not going to be installed
               Recommends: openoffice.org-filter-binfilter but it is not going to be installed
E: Broken packages

```Could someone please give a step-by-step description and then make this thread sticky, since I've come across numerous posts like this.

I have tried to remove any 'ure' packages but that didn't help. :(

Please help!

---

### Post by bodhi.zazen on 2011-04-19
Try :

```
sudo apt-get update && sudo apt-get install openoffice.org
```

---

### Post by Elvis99 on 2011-04-19
Will do, thanks for the advice. I've managed to install and to run Libreoffice, but I'm dazzled about the difficulties the switch caused...

---

### Post by bodhi.zazen on 2011-04-19
It is a large package and I do not often use it, so I see no need to rip out OpenOffice and install LibreOffice.

Ubuntu 11.04 and F15 will both include LibreOffice soon enough =)

---

### Post by Hagar Delest on 2011-04-20
You can install the vanilla versions in parallel without any problem, see [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

