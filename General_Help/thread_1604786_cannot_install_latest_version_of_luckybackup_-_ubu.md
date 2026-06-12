---
title: "cannot install latest version of luckybackup - ubuntu gives error"
date: 2010-10-24
forum: General Help
---

### Post by fuzzylogic25 on 2010-10-24
I tried to install the latest luckybackup software, from the official site (it was a deb package created for ubuntu 10.04, which is the version im using) and this error occured:

=====================================================
Unpacking luckybackup (from .../luckybackup_0.4.3-1_i386.lucid.deb)...
dpkg: error processing /home/john/Downloads/luckybackup_0.4.3-1_i386.lucid.deb (--install):
trying to overwrite '/usr/share/luckybackup/translations/luckybackup_it.qm', which is also in package luckybackup-data 0:0.3.5-1ubuntu1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for menu ...
Errors were encountered while processing:
/home/john/Downloads/luckybackup_0.4.3-1_i386.lucid.deb

=====================================================

now initially, i had installed luckybackup from the ubuntu repository using sudo apt-get install luckybackup. but it was an old version (0.3.5 i think) so i removed it using sudo apt-get remove luckybackup.

I also removed the folder /usr/share/luckybackup/translations and all its contents. but i still get this problem.

what does this problem mean and how do i fix it? thanks!

---

### Post by fuzzylogic25 on 2011-04-28
anyone know of a solution to this problem? i tried again and it still occurs!

---

### Post by plucky on 2011-04-28
> I also removed the folder /usr/share/luckybackup/translations and all its contents. but i still get this problem.

what does this problem mean and how do i fix it? thanks! 

You should use Synaptic package manager to remove the package as you should find there is also a package called luckybackup-data which is what the message is complaining about.

> dpkg: error processing /home/john/Downloads/luckybackup_0.4.3-1_i386.lucid.deb (--install):
trying to overwrite '/usr/share/luckybackup/translations/luckybackup_it.qm', which is also in package **luckybackup-data 0:0.3.5-1ubuntu1**

Also you could try adding the PPA and going down that route.

See [Here](https://launchpad.net/~luckybackup-maintainers/+archive/ppa)

Good Luck

---

