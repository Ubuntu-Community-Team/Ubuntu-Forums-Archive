---
title: "Help! Local Mirror not working properly"
date: 2010-03-17
forum: General Help
---

### Post by lais on 2010-03-17
We have a local repository in my uni from where we download updates for Ubuntu. Lately, I have noticed that updates in the Kubuntu PPA and Kubuntu Backport PPA are not getting downloaded in the local repo. The mirror.list file is given below. Can someone please figure out what the the problem is? Thanks in advance.

```
############# config ##################
#
# set base_path    /var/spool/apt-mirror
#
# if you change the base path you must create the directories below with write privlages
#
# set mirror_path  $base_path/mirror
# set skel_path    $base_path/skel
# set var_path     $base_path/var
# set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
set nthreads     20
set tilde 0
#
############# end config ##############

deb http://archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu hardy-proposed main restricted universe multiverse

#deb http://archive.ubuntu.com/ubuntu jaunty main restricted universe multiverse
#deb http://archive.ubuntu.com/ubuntu jaunty-updates main restricted universe multiverse
#deb http://archive.ubuntu.com/ubuntu jaunty-backports main restricted universe multiverse
#deb http://archive.ubuntu.com/ubuntu jaunty-security main restricted universe multiverse
#deb http://archive.ubuntu.com/ubuntu jaunty-proposed main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu karmic main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu karmic-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu karmic-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu karmic-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu karmic-proposed main restricted universe multiverse

deb http://packages.medibuntu.org/ hardy free non-free
#deb http://packages.medibuntu.org/ jaunty free non-free
deb http://packages.medibuntu.org/ karmic free non-free

deb http://wine.budgetdedicated.com/apt hardy main
deb http://wine.budgetdedicated.com/apt jaunty main
#deb http://wine.budgetdedicated.com/apt karmic main

#Fetch Wine Fonts
#deb http://wine.sourceforge.net/apt/ binary/

clean http://archive.ubuntu.com/ubuntu

#deb http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu jaunty main
#deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main

deb http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu karmic main
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main

#Added for themes
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu karmic main
```

---

