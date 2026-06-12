---
title: "About Installing Apt packages on fresh install again"
date: 2011-06-13
forum: General Help
---

### Post by CyberMatrix on 2011-06-13
Hi this my first post.Please forgive me if put in wrong section.

So my question is that i always have to install packages from software center whenever i install Ubuntu fresh.Of course they be saved cache folder in var so.

My question is that is there any software or package with which i install them on same version of Ubuntu as before without having downloading and installing them again?If i save this packages on anywhere on my drive..and if again formatted and want reinstall them with resolving there dependency as well.Package will in package in same as when we install terminal or software center...does any have some kind magic for this...:D
 
Because its really time consuming and also i have slow Internet connection speed.
believe me just 512 kbps(60 Kb/s)...ohh ya this sucks..:D

---

### Post by gmargo on 2011-06-13
Have a look at the **apt-cacher-ng** package.

[http://packages.ubuntu.com/natty/apt-cacher-ng](http://packages.ubuntu.com/natty/apt-cacher-ng)

---

### Post by CyberMatrix on 2011-06-14
If possible can you guide me how to use it...thanks...still looking some GUI based package if anyone knows

---

### Post by plucky on 2011-06-14
> My question is that is there any software or package with which i install them on same version of Ubuntu as before without having downloading and installing them again?If i save this packages on anywhere on my drive..and if again formatted and want reinstall them with resolving there dependency as well.Package will in package in same as when we install terminal or software center...does any have some kind magic for this...

Try [AptonCd](http://aptoncd.sourceforge.net/) which is in the repositories.

The downloaded .deb files are stored in /var/cache/apt/archives folder.

Good Luck

---

### Post by CyberMatrix on 2011-06-18
> **plucky said:**
> Try [AptonCd]("http://aptoncd.sourceforge.net/") which is in the repositories.

The downloaded .deb files are stored in /var/cache/apt/archives folder.

Good Luck
Ohh yes i know that one but it does not install packages with there dependencies satisfied

---

