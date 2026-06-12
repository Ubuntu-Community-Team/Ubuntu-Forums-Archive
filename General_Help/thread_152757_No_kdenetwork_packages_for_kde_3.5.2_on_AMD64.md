---
title: "No kdenetwork packages for kde 3.5.2 on AMD64"
date: 2006-03-30
forum: General Help
---

### Post by angelillo on 2006-03-30
Hello,

I am using Breezy on AMD64. 
Yesterday i upgraded to KDE 3.5.2 (from 3.5.1) using this repository:

deb [http://kubuntu.org/packages/kde352](http://kubuntu.org/packages/kde352) breezy main

After upgrading (tried "dist-upgrade" too), i noticed there are several packages missing under AMD64 architecture (i.e. those under directory "kdenetwork"):

[FONT="Lucida Console"][SIZE="1"]$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  kdenetwork
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.[/SIZE][/FONT]


apt-get install kdenetwork results in the following message:
[SIZE="1"][FONT="Lucida Console"][...]
The following packages have unmet dependencies:
  kdenetwork: Depends: dcoprss (>= 4:3.5.2-0ubuntu0breezy1) but 4:3.5.1-0ubuntu0breezy1 is to be installed
              Depends: kdenetwork-kfile-plugins (>= 4:3.5.2-0ubuntu0breezy1) but 4:3.5.1-0ubuntu0breezy1 is to be installed
              Depends: kdict (>= 4:3.5.2-0ubuntu0breezy1) but 4:3.5.1-0ubuntu0breezy1 is to be installed
              Depends: kget (>= 4:3.5.2-0ubuntu0breezy1) but 4:3.5.1-0ubuntu0breezy1 is to be installed
              Depends: knewsticker (>= 4:3.5.2-0ubuntu0breezy1) but 4:3.5.1-0ubuntu0breezy1 is to be installed
              Depends: kopete (>= 4:3.5.2-0ubuntu0breezy1) but 4:3.5.1-0ubuntu0breezy1 is to be installed
              Depends: kpf (>= 4:3.5.2-0ubuntu0breezy1) but 4:3.5.1-0ubuntu0breezy1 is to be installed
              Depends: kppp (>= 4:3.5.2-0ubuntu0breezy1) but 4:3.5.1-0ubuntu0breezy1 is to be installed
              Depends: krdc (>= 4:3.5.2-0ubuntu0breezy1) but 4:3.5.1-0ubuntu0breezy1 is to be installed
              Depends: krfb (>= 4:3.5.2-0ubuntu0breezy1) but 4:3.5.1-0ubuntu0breezy1 is to be installed
              Depends: ksirc (>= 4:3.5.2-0ubuntu0breezy1) but 4:3.5.1-0ubuntu0breezy1 is to be installed
              Depends: kwifimanager (>= 4:3.5.2-0ubuntu0breezy1) but 4:3.5.1-0ubuntu0breezy1 is to be installed
              Depends: librss1 (>= 4:3.5.2-0ubuntu0breezy1) but 4:3.5.1-0ubuntu0breezy1 is to be installed
              Depends: kdnssd (>= 4:3.5.2-0ubuntu0breezy1) but 4:3.5.1-0ubuntu0breezy1 is to be installed
E: Broken packages
[/FONT][/SIZE]

Is it a bug? Anyone knows why are those packages missing?

---

