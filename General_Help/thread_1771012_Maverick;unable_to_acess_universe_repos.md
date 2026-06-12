---
title: "Maverick;unable to acess universe repos"
date: 2011-05-29
forum: General Help
---

### Post by srisharan on 2011-05-29
I finally managed to convince my dad to try Ubuntu and installed maverick in his desktop :D.I myself am new to Linux(6 months old) and found the experience refreshing.Now in my dads computer although I have enabled the universe repos neither the synaptic or the software center or the apt-get seem to be able to access them.Here is my /etc/apt/source.list.Any help will be greatly appreciated

## deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository
## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://ubuntuarchive.hnsdc.com/ubuntu/](http://ubuntuarchive.hnsdc.com/ubuntu/) maverick main universe restricted multiverse

---

### Post by linuxinstalledfromhdd on 2011-05-29
Here you go.. This should help speed up the process:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by srisharan on 2011-05-29
tried adding repos in the way it siad.no change :(,same problem

---

### Post by linuxinstalledfromhdd on 2011-05-29
In terminal run:

sudo apt-get update
sudo apt-get upgrade

Do you get any errors?

If it works, go to back to the walkthough and look for adding independent and partner repositories. And install them with the command line from terminal.

---

### Post by srisharan on 2011-05-30
Yes I still get errors.By way is there is way to apt-get update only the universe repos?

---

