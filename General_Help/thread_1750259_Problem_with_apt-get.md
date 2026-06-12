---
title: "Problem with apt-get"
date: 2011-05-05
forum: General Help
---

### Post by nbrochu on 2011-05-05
Hello, every time i try to install a package it fails. I get this output. 


Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 consolekit : Depends: dbus (>= 1.1.2) but it is not going to be installed
 dbus-x11 : Depends: dbus but it is not going to be installed
 gconf2-common : Depends: dbus but it is not going to be installed
 libgnomevfs2-0 : Depends: dbus (>= 0.90) but it is not going to be installed
                  Recommends: libgnomevfs2-extra but it is not going to be installed
 libice6 : Depends: x11-common but it is not going to be installed
 libxres1 : Depends: x11-common but it is not going to be installed
 samba : Depends: samba-common (= 2:3.5.4~dfsg-1ubuntu8.4) but it is not going to be installed
         Depends: libwbclient0 (= 2:3.5.4~dfsg-1ubuntu8.4) but it is not going to be installed
         Depends: libtalloc2 (>= 2.0.0) but it is not going to be installed
         Depends: update-inetd but it is not going to be installed
         Depends: samba-common-bin but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

i did fun the apt-get -f install and it is still doing the same thing. Any ideas or solutions would be very help full.

---

### Post by dino99 on 2011-05-05
try:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo dpkg --configure -a

are you using only the genuine repo ? or have installed some extra third parties repo (like ppa) ?

its not an apt-get issue, it works fine, but you try to upgrade conflicting packages (dependencies releases non compatible)

---

### Post by brandonmcghee on 2011-05-05
What version of Ubuntu do you have installed and is it an Upgrade or Fresh Install?

---

### Post by nbrochu on 2011-05-05
its 10.10 server and when i run sudo apt-get auto remove i get this message.


nick@ubuntu:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 consolekit : Depends: dbus (>= 1.1.2) but it is not installed
 dbus-x11 : Depends: dbus but it is not installed
 gconf2-common : Depends: dbus but it is not installed
 libgnomevfs2-0 : Depends: dbus (>= 0.90) but it is not installed
                  Recommends: libgnomevfs2-extra but it is not installed
 libice6 : Depends: x11-common but it is not installed
 libxres1 : Depends: x11-common but it is not installed
E: Unmet dependencies. Try using -f.

---

### Post by dino99 on 2011-05-05
post your /etc/apt/sources.list here please

---

### Post by nbrochu on 2011-05-05
#
# deb cdrom:[Ubuntu-Server 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted

#deb cdrom:[Ubuntu-Server 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse

---

### Post by dino99 on 2011-05-05
hm that seem correct, can you switch on "main" server instead of "us" one (into synaptic)?

clear the sources:

sudo rm /var/cache/apt/archives/*
 (no worry about the complain)

then update again

---

### Post by nbrochu on 2011-05-05
i rm that file but the problem still exist.

---

### Post by nbrochu on 2011-05-05
> **dino99 said:**
> hm that seem correct, can you switch on "main" server instead of "us" one (into synaptic)?

clear the sources:

sudo rm /var/cache/apt/archives/*
 (no worry about the complain)

then update again

How do i go about switching on main server?

---

### Post by dino99 on 2011-05-05
> **nbrochu said:**
> How do i go about switching on main server?

open from top menu: system admin synaptic config repo, and select "download from: main server"

---

### Post by nbrochu on 2011-05-05
i dont have the gui installed. thats what im trying to install but it wont let me due to these issues.

---

### Post by dino99 on 2011-05-05
then try aptitude instead of apt-get (but i doubt you get better results)

have you cleaned /var/cache/.... ?

---

### Post by nbrochu on 2011-05-05
yes i did. What could have caused this issue?

---

### Post by NoNameWill on 2011-05-05
Have you tried just installing the dbus package? I had something similar happen a few weeks ago with 10.04. Someone figured out to install just a dependency of one of the packages. That worked for me and others it affected.

---

