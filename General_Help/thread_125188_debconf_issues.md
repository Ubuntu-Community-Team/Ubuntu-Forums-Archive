---
title: "debconf issues"
date: 2006-02-03
forum: General Help
---

### Post by Reggie on 2006-02-03
Hi,

I had some problems getting apt to work back after a package failed to install. Whenever I wanted to install a package apt said that I had to fix the packages by using apt-get -f install. But when I did that it failed too. So I read somewhere that when you remove /var/lib/dpkg/status and touch it again all problems should be solved.

Whenever I install a new package now I get the following errors:

```
 debconf: apt-extracttemplates failed: Bad file descriptorE: Cannot get debconf version. Is debconf installed ?
debconf: apt-extracttemplates failed: Bad file descriptorE: Cannot get debconf version. Is debconf installed ?
debconf: apt-extracttemplates failed: Bad file descriptorE: Cannot get debconf version. Is debconf installed ?

dpkg not recorded as isntalled, cannot check for epoch support !

```

Do I have to give the "status" file permissions ? What can I do to solve this ?

---

### Post by cniharral on 2006-04-27
Hi,

  Well, I think I had the same problem after a filesystem crash that maybe caused a file corruption in one of the files needed for apt, dpkg or debconf, don't know exactly.

  And after some headaches trying to solve it moving the directories /var/lib/apt, /var/cache/apt to an old version and trying to recover them creating new directories, I came to the solution when I opened the file /var/lib/dpkg/status and realized that it was nearly empty, so I filled it with some of the information that was going to be essential for the recovery of the system. In other words I put the following lines on it (I had to take a look to another debian-like system installation):

Package: dpkg
Essential: yes
Status: install ok installed
Priority: required
Section: base
Version: 1.13.10

  And after that, I did:

> apt-get install --reinstall dpkg

  Before doing all this stuff, I have confirmed that the packages dpkg and debconf were installed on the system, and so they were.

  When you finished reinstalling dpkg, surely you'll have to reinstall all the packages on your system, and it will take you a long time, but if you have a fast internet connection, it will not be any problem at all except for the time spent.

  I reinstalled all the packages by using aptitude tool.

  Hope this helps you or anyone with the same problem.

Regards.

   Carlos Niharra López

"Something wonderful is going to happen"  - 2010: Oddysey 2

"Everyday, there's always something wonderful to happen ..."

---

