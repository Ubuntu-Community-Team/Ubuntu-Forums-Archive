---
title: "Problem installing ia32-libs - Google Earth"
date: 2012-08-23
forum: General Help
---

### Post by JCM_Pico on 2012-08-23
Hello there,

I've found an interesting problem today... after installing every thing I use to need in my Kubuntu install... I've found that google-earth was missing. However I was shore it was installed properly... So, I started to get things done and try to reinstall it again....
BUT... when trying to install it I've found that lots of packages and applications would be removed due to the dependence o ia32-lib....

```
sudo dpkg -i google-earth-stable_current_amd64.deb 
Selecting previously unselected package google-earth-stable.
(Reading database ... 264233 files and directories currently installed.)
Unpacking google-earth-stable (from google-earth-stable_current_amd64.deb) ...
dpkg: dependency problems prevent configuration of google-earth-stable:
 google-earth-stable depends on ia32-libs; however:
  Package ia32-libs is not installed.
dpkg: error processing google-earth-stable (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 google-earth-stable
jcmteixeira@jcmteixeira-Linux:~/Downloads$ sudo apt-get install ia32-libs 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
jcmteixeira@jcmteixeira-Linux:~/Downloads$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  melt libpam-winbind ttf-umefont dvgrab swh-plugins libmlt++3 libcapi20-3 dvdauthor unixodbc kdenlive-data lib32asound2 recordmydesktop wine-gecko1.4 wine-gecko1.4:i386
  libgif4:i386 ttf-unfonts-core libmpg123-0 winbind libodbc1 fonts-droid ttf-droid
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ia32-libs ia32-libs-multiarch:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386 libglu1-mesa:i386 libqt4-opengl:i386
Suggested packages:
  libpam-ldap:i386 libpam-winbind:i386 libnss-ldap:i386 libglide3:i386
The following packages will be REMOVED:
  kdenlive kinfocenter kubuntu-desktop libglu1-mesa libvisual-0.4-plugins xorg                                                                                               
The following NEW packages will be installed:                                                                                                                                
  ia32-libs ia32-libs-multiarch:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386 libglu1-mesa:i386 libqt4-opengl:i386                                       
0 upgraded, 7 newly installed, 6 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 25.1 MB/25.4 MB of archives.
After this operation, 86.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? n 

```

Is there any way to go around this?

---

### Post by matt_symes on 2012-08-23
Hi

I don't use Kubutu so i may not be much help here. However, there are others here that use Kubuntu so, hopefully, they can chip in some information.

In the mean time, it may be worth checking your sources files to make sure there is no problem there.

Can you post the output, from the terminal, of..

```
grep -r ^ /etc/apt/sources.list{,.d/*}
```

You can copy and past the results from the terminal into your next post.

BTW: There is a Kubuntu forum.

[http://www.kubuntuforums.net/](http://www.kubuntuforums.net/)

Kind regards

---

### Post by JCM_Pico on 2012-08-23
grep -r ^ /etc/apt/sources.list{,.d/*}

```
/etc/apt/sources.list:# deb cdrom:[Kubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120423)]/ dists/precise/main/binary-i386/
/etc/apt/sources.list:
/etc/apt/sources.list:# deb cdrom:[Kubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120423)]/ dists/precise/restricted/binary-i386/
/etc/apt/sources.list:# deb cdrom:[Kubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120423)]/ precise main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
/etc/apt/sources.list:# newer versions of the distribution.
/etc/apt/sources.list:deb http://pt.archive.ubuntu.com/ubuntu/ precise main restricted
/etc/apt/sources.list:deb-src http://pt.archive.ubuntu.com/ubuntu/ precise main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:## Major bug fix updates produced after the final release of the
/etc/apt/sources.list:## distribution.
/etc/apt/sources.list:deb http://pt.archive.ubuntu.com/ubuntu/ precise-updates main restricted
/etc/apt/sources.list:deb-src http://pt.archive.ubuntu.com/ubuntu/ precise-updates main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
/etc/apt/sources.list:## team. Also, please note that software in universe WILL NOT receive any
/etc/apt/sources.list:## review or updates from the Ubuntu security team.
/etc/apt/sources.list:deb http://pt.archive.ubuntu.com/ubuntu/ precise universe
/etc/apt/sources.list:deb-src http://pt.archive.ubuntu.com/ubuntu/ precise universe
/etc/apt/sources.list:deb http://pt.archive.ubuntu.com/ubuntu/ precise-updates universe
/etc/apt/sources.list:deb-src http://pt.archive.ubuntu.com/ubuntu/ precise-updates universe
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
/etc/apt/sources.list:## team, and may not be under a free licence. Please satisfy yourself as to 
/etc/apt/sources.list:## your rights to use the software. Also, please note that software in 
/etc/apt/sources.list:## multiverse WILL NOT receive any review or updates from the Ubuntu
/etc/apt/sources.list:## security team.
/etc/apt/sources.list:deb http://pt.archive.ubuntu.com/ubuntu/ precise multiverse
/etc/apt/sources.list:deb-src http://pt.archive.ubuntu.com/ubuntu/ precise multiverse
/etc/apt/sources.list:deb http://pt.archive.ubuntu.com/ubuntu/ precise-updates multiverse
/etc/apt/sources.list:deb-src http://pt.archive.ubuntu.com/ubuntu/ precise-updates multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository may not have been tested as
/etc/apt/sources.list:## extensively as that contained in the main release, although it includes
/etc/apt/sources.list:## newer versions of some applications which may provide useful features.
/etc/apt/sources.list:## Also, please note that software in backports WILL NOT receive any review
/etc/apt/sources.list:## or updates from the Ubuntu security team.
/etc/apt/sources.list:deb http://pt.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src http://pt.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu precise-security main restricted
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu precise-security universe
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu precise-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu precise-security multiverse
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## Uncomment the following two lines to add software from Canonical's
/etc/apt/sources.list:## 'partner' repository.
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by Canonical and the
/etc/apt/sources.list:## respective vendors as a service to Ubuntu users.
/etc/apt/sources.list:# deb http://archive.canonical.com/ubuntu precise partner
/etc/apt/sources.list:# deb-src http://archive.canonical.com/ubuntu precise partner
/etc/apt/sources.list:
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by third-party
/etc/apt/sources.list:## developers who want to ship their latest software.
/etc/apt/sources.list:deb http://extras.ubuntu.com/ubuntu precise main
/etc/apt/sources.list:deb-src http://extras.ubuntu.com/ubuntu precise main
/etc/apt/sources.list.d/benoitg-akonadigoogle-daily-precise.list:deb http://ppa.launchpad.net/benoitg/akonadigoogle-daily/ubuntu precise main
/etc/apt/sources.list.d/benoitg-akonadigoogle-daily-precise.list:deb-src http://ppa.launchpad.net/benoitg/akonadigoogle-daily/ubuntu precise main
/etc/apt/sources.list.d/benoitg-akonadigoogle-daily-precise.list.save:deb http://ppa.launchpad.net/benoitg/akonadigoogle-daily/ubuntu precise main
/etc/apt/sources.list.d/benoitg-akonadigoogle-daily-precise.list.save:deb-src http://ppa.launchpad.net/benoitg/akonadigoogle-daily/ubuntu precise main
/etc/apt/sources.list.d/chasedouglas-clickpad-precise.list:deb http://ppa.launchpad.net/chasedouglas/clickpad/ubuntu precise main
/etc/apt/sources.list.d/chasedouglas-clickpad-precise.list:deb-src http://ppa.launchpad.net/chasedouglas/clickpad/ubuntu precise main
/etc/apt/sources.list.d/chasedouglas-clickpad-precise.list.save:deb http://ppa.launchpad.net/chasedouglas/clickpad/ubuntu precise main
/etc/apt/sources.list.d/chasedouglas-clickpad-precise.list.save:deb-src http://ppa.launchpad.net/chasedouglas/clickpad/ubuntu precise main
/etc/apt/sources.list.d/colin-king-powermanagement-precise.list:deb http://ppa.launchpad.net/colin-king/powermanagement/ubuntu precise main
/etc/apt/sources.list.d/colin-king-powermanagement-precise.list:deb-src http://ppa.launchpad.net/colin-king/powermanagement/ubuntu precise main
/etc/apt/sources.list.d/colin-king-powermanagement-precise.list.save:deb http://ppa.launchpad.net/colin-king/powermanagement/ubuntu precise main
/etc/apt/sources.list.d/colin-king-powermanagement-precise.list.save:deb-src http://ppa.launchpad.net/colin-king/powermanagement/ubuntu precise main
/etc/apt/sources.list.d/dropbox.list:deb http://linux.dropbox.com/ubuntu precise main
/etc/apt/sources.list.d/dropbox.list.save:deb http://linux.dropbox.com/ubuntu precise main
/etc/apt/sources.list.d/google-chrome.list:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-chrome.list:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-chrome.list:deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list.save:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-chrome.list.save:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-chrome.list.save:deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-earth.list:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-earth.list:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-earth.list:deb http://dl.google.com/linux/earth/deb/ stable main
/etc/apt/sources.list.d/google-earth.list.save:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-earth.list.save:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-earth.list.save:deb http://dl.google.com/linux/earth/deb/ stable main
/etc/apt/sources.list.d/xorg-edgers-ppa-precise.list:deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu precise main
/etc/apt/sources.list.d/xorg-edgers-ppa-precise.list:deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu precise main
/etc/apt/sources.list.d/xorg-edgers-ppa-precise.list.save:deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu precise main
/etc/apt/sources.list.d/xorg-edgers-ppa-precise.list.save:# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu precise main
```

Thanks for the reply =)

---

### Post by matt_symes on 2012-08-23
Hi

> 
Thanks for the reply =)

No sure if i can help yet :D. 

I have noticed that one of the packages it wants to remove is xorg and you are using the xorg-edgers ppa.

I am wondering if that is creating a problem for you. Any reason you are using that ppa ?

Kind regards

---

### Post by JCM_Pico on 2012-08-23
Yes I'm using xorg-edger ppa for hardware reason... with asus ux31 it helps to get the touchpad working properly

---

### Post by matt_symes on 2012-08-23
Hi

As i don't use the xorg-edger's ppa or Kubuntu, i should bow out of this thread.

I hope someone else chimes in for you.

Kind regards

---

