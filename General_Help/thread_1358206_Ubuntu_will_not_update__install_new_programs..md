---
title: "Ubuntu will not update / install new programs."
date: 2009-12-18
forum: General Help
---

### Post by zozza on 2009-12-18
I no longer seem able to update or install programs.

Using the GUI update manager after clicking "install updates" the programs download very very slowly (100 bytes / sec for example) and then get stuck.

Using sudo apt-get install Ubuntu starts the download, quickly slows down, and the text on the right tells me it will take 6 hours or something silly to download a few MB.

How can I deal with this?  It started yesterday morning so is a persistent problem. 

The problem occurs with apt-get, synaptic package manager, and update manager.

Thanks.

---

### Post by konqueror7 on 2009-12-18
> **zozza said:**
> I no longer seem able to update or install programs.

Using the GUI update manager after clicking "install updates" the programs download very very slowly (100 bytes / sec for example) and then get stuck.

Using sudo apt-get install Ubuntu starts the download, quickly slows down, and the text on the right tells me it will take 6 hours or something silly to download a few MB.

How can I deal with this?  It started yesterday morning so is a persistent problem. 

The problem occurs with apt-get, synaptic package manager, and update manager.

Thanks.

try changing your download server, go to *System > Administration > Software Sources*. in the *Ubuntu Software* tab, select *Download From* then *Others*. proceed by *Select Best Server*. see if that helps.

---

### Post by nibirumarduk on 2009-12-18
Zozza do as konqueror7 has suggested. Also do take a look at [http://ubuntuforums.org/showthread.php?t=1358078](http://ubuntuforums.org/showthread.php?t=1358078) . Could be useful.

---

### Post by 3rdalbum on 2009-12-18
If you're using mobile broadband, this is a common issue that I've observed on Ubuntu and Windows 7. Mobile broadband works great in short bursts, but for large files any interruption or speed-switching will cause the download to fail.

Try using a cable or ADSL internet connection.

---

### Post by zozza on 2009-12-18
Thanks guys - worked perfectly.  I am now using a server in Japan (I am in the UK).

Two questions:

First, what happened?  Why did the upgrades and installations stop working from the previous download site?

Second I have three questions about my sources.list file (below).

a) what is the difference between deb and deb-src?
b) why does deb security not have a corresponding deb-src security whereas deb update does have a deb-src update?
c) why on upgrade to 9.10 was Skype commented out?  What if I want to keep using it?

deb [http://ftp.jaist.ac.jp/pub/Linux/ubuntu/](http://ftp.jaist.ac.jp/pub/Linux/ubuntu/) karmic main restricted
deb-src [http://ftp.jaist.ac.jp/pub/Linux/ubuntu/](http://ftp.jaist.ac.jp/pub/Linux/ubuntu/) karmic main restricted #Added by software-properties

deb [http://ftp.jaist.ac.jp/pub/Linux/ubuntu/](http://ftp.jaist.ac.jp/pub/Linux/ubuntu/) karmic-updates main restricted
deb-src [http://ftp.jaist.ac.jp/pub/Linux/ubuntu/](http://ftp.jaist.ac.jp/pub/Linux/ubuntu/) karmic multiverse universe #Added by software-properties
deb-src [http://ftp.jaist.ac.jp/pub/Linux/ubuntu/](http://ftp.jaist.ac.jp/pub/Linux/ubuntu/) karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ftp.jaist.ac.jp/pub/Linux/ubuntu/](http://ftp.jaist.ac.jp/pub/Linux/ubuntu/) karmic universe
deb [http://ftp.jaist.ac.jp/pub/Linux/ubuntu/](http://ftp.jaist.ac.jp/pub/Linux/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ftp.jaist.ac.jp/pub/Linux/ubuntu/](http://ftp.jaist.ac.jp/pub/Linux/ubuntu/) karmic multiverse
deb [http://ftp.jaist.ac.jp/pub/Linux/ubuntu/](http://ftp.jaist.ac.jp/pub/Linux/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

# deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free # disabled on upgrade to karmic
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security restricted main multiverse universe

---

### Post by konqueror7 on 2009-12-19
> **zozza said:**
> Thanks guys - worked perfectly.  I am now using a server in Japan (I am in the UK).

Two questions:

First, what happened?  Why did the upgrades and installations stop working from the previous download site?

Second I have three questions about my sources.list file (below).

a) what is the difference between deb and deb-src?
b) why does deb security not have a corresponding deb-src security whereas deb update does have a deb-src update?
c) why on upgrade to 9.10 was Skype commented out?  What if I want to keep using it?

deb [http://ftp.jaist.ac.jp/pub/Linux/ubuntu/](http://ftp.jaist.ac.jp/pub/Linux/ubuntu/) karmic main restricted
deb-src [http://ftp.jaist.ac.jp/pub/Linux/ubuntu/](http://ftp.jaist.ac.jp/pub/Linux/ubuntu/) karmic main restricted #Added by software-properties

deb [http://ftp.jaist.ac.jp/pub/Linux/ubuntu/](http://ftp.jaist.ac.jp/pub/Linux/ubuntu/) karmic-updates main restricted
deb-src [http://ftp.jaist.ac.jp/pub/Linux/ubuntu/](http://ftp.jaist.ac.jp/pub/Linux/ubuntu/) karmic multiverse universe #Added by software-properties
deb-src [http://ftp.jaist.ac.jp/pub/Linux/ubuntu/](http://ftp.jaist.ac.jp/pub/Linux/ubuntu/) karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ftp.jaist.ac.jp/pub/Linux/ubuntu/](http://ftp.jaist.ac.jp/pub/Linux/ubuntu/) karmic universe
deb [http://ftp.jaist.ac.jp/pub/Linux/ubuntu/](http://ftp.jaist.ac.jp/pub/Linux/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ftp.jaist.ac.jp/pub/Linux/ubuntu/](http://ftp.jaist.ac.jp/pub/Linux/ubuntu/) karmic multiverse
deb [http://ftp.jaist.ac.jp/pub/Linux/ubuntu/](http://ftp.jaist.ac.jp/pub/Linux/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

# deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free # disabled on upgrade to karmic
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security restricted main multiverse universe

a.) *deb* are the binaries or the compiled versions of the program which you can directly execute. on the other hand, *deb-src* are source codes of the said programs, which you may need to compile first (if there are no binaries) to execute them later on.

b.) packages are provided by the community, so they decide what is included or excluded.

c.) on upgrade, ubuntu temporarily disables 3rd party sources to prevent conflicts after the upgrade. as for skype, you can uncomment them again since the sources are generic and would not conflict with the current release.

for more details regarding sources and repos, [read this]("https://help.ubuntu.com/community/Repositories/Ubuntu"). :P

---

