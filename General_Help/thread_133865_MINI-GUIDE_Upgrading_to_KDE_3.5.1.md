---
title: "MINI-GUIDE: Upgrading to KDE 3.5.1"
date: 2006-02-20
forum: General Help
---

### Post by Jucato on 2006-02-20
MINI-GUIDE: Upgrading to KDE 3.5.1

I'm creating a sort of mini-guide to upgrading to KDE 3.5.1, seeing that there will be no Kubuntu installer released before Dapper is released in Apri (which is still 2 months away...). Hope this helps a bit.

**DISCLAIMER**: I'm basing this guide on my own experience and on the experiences of others who have had trouble upgrading their system. I cannot guarantee 100% success, since I do not have the resouces to test each and every situation. I'm not also claiming to be an expert. Hopefully, this thread could be a main thread for upgrading KDE to 3.5.1. If you have any questions/problems, feel free to ask.

Ok, let's get to business.

1. Install kdebase. **This is important!!**. kdebase contains packages not installed by Kubuntu by default but are needed by KDE in order to upgrade successfully. If you do not install this, some packages will be held back, especially kdelibs-bin and/or kdelibs4. The Kubuntu devs have their reasons why kdebase is not installed by default in the kubuntu-desktop metapackage. Be that as it may, this metapackage is still needed to successfully upgrade KDE. Besides, most of the 

**Note:** For those planning to install kde-devel, see Problems #2 at the bottom of the post before proceeding:

2. the KDE 3.5.1 package is signed by Jonathan Riddle's key, so you have to download and add that key.
- to get the key:
```
wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg
```
- and to add it:
```
sudo apt-key add kubuntu-packages-jriddell-key.gpg
```

3. Add/enable the necessary repositories;
NOTE: you only need to enable one. They are just mirrors. If you are having trouble with one, you can try out the others.
- open up your /etc/apt/souces.list (or use your favorite package manager) and add these. Again, enable only one at a time so that there will be no conflicts.
These are from the the Kubuntu site:
```
deb http://kubuntu.org/packages/kde351 breezy main
deb ftp://bolugftp.uni-bonn.de/pub/kde/stable/3.5.1/kubuntu breezy main
deb http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/3.5.1/kubuntu breezy main
deb http://mirror.cc.columbia.edu/pub/software/kde/stable/3.5.1/kubuntu breezy main
```
-or you can just use these two so that you won't have to change your sources.list everytime a new KDE version comes out (taken from [this post](http://www.ubuntuforums.org/showpost.php?p=733432&postcount=66), my thanks to kaydot@kubuntu):
```
## LATEST KDE VERSION FROM kubuntu.org
deb http://kubuntu.org/packages/kde-latest breezy main
deb-src http://kubuntu.org/packages/kde-latest breezy main
```

4. Now for the long part: Update your repositories and Upgrade your system:
```
sudo apt-get update
sudo apt-get upgrade
```
If some packages are held back, you could also do a dist-upgrade
```
sudo apt-get dist-upgrade
```

PROBLEMS:
Here are some of the problems I have seen and have been able to help solve:

1. kdelibs and/or kdelibs4c2 are always held back:
- What to do: if you followed step #1 and installed kdebase, it's probable that this won't happen. If it still does, try installing the kdelibs metapackage as well. But again, this probably won't happen anymore if kdebase is installed.

2. kde-devel will get broken if I update to 3.5.1
- I guess this might be a problem since kdebase is found in the main repositories, while kde-devel is in the universe repositories. One workaround I found here was to install kde-devel first before upgrading.
- Another probable solution (unconfirmed as of this writing) is to install kdebase-dev, even after upgrading to KDE 3.5.1, as this will install the necessary packages for kde-deve.

I hope this helps people with upgrading to KDE 3.5.1. As to why they should upgrade? Well, KDE 3.5.1 fixes some of the bugs found in the KDE 3.4.x (which is the default Kubuntu Breezy version). It, however, changes somethings like HAL and displaying mounted partitions in media:/ (but that's another topic).

----------------------------------------------
Keywords: (to help facilitate searching)
help, upgrade, upgrading, update, updating, install, installing, KDE, 3.5.1, 3.5, 3.4, hold, held, holding, problems, problems, kde-devel, kdelibs, kdelibs-bin, kdelibs4, kdelibs4c2, break, broken, breaking.

---

