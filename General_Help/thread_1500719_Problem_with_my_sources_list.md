---
title: "Problem with my sources list?"
date: 2010-06-03
forum: General Help
---

### Post by sports fan Matt on 2010-06-03
I have a feeling that something is not right with my sources list, can ya'll take a look? feels incomplete

 deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates universe

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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-proposed restricted main universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-proposed restricted main universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-backports restricted main universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-backports restricted main universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid restricted
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free main
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing non-free main
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) lucid main
deb [http://ppa.launchpad.net/improved-lcd-filtering/ppa/ubuntu](http://ppa.launchpad.net/improved-lcd-filtering/ppa/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/improved-lcd-filtering/ppa/ubuntu](http://ppa.launchpad.net/improved-lcd-filtering/ppa/ubuntu) lucid main
deb [http://ppa.launchpad.net/ricotz/testing/ubuntu](http://ppa.launchpad.net/ricotz/testing/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/ricotz/testing/ubuntu](http://ppa.launchpad.net/ricotz/testing/ubuntu) lucid main
deb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/lucid-updates](http://us.archive.ubuntu.com/ubuntu/lucid-updates) main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-backports restricted
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security restricted

---

### Post by barney385 on 2010-06-03
Looks like you need to add Medibuntu repos.

What's NB software?

Like the warning says, you need to uncomment (#) those two specified lines.

---

### Post by sports fan Matt on 2010-06-03
I'm not sure,  but I wonder if this one I just generated would work better?

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted universe multiverse 

###### Ubuntu Update Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### Breathe Icon Set - [https://edge.launchpad.net/~breathe-dev/+archive/ppa](https://edge.launchpad.net/~breathe-dev/+archive/ppa)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 45FFBBBA
deb [http://ppa.launchpad.net/breathe-dev/ppa/ubuntu](http://ppa.launchpad.net/breathe-dev/ppa/ubuntu) lucid main

#### GetDeb - [http://www.getdeb.net](http://www.getdeb.net)
## Run this command: wget -q -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb apps

#### Medibuntu - [http://www.medibuntu.org/](http://www.medibuntu.org/) 
## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free 

#### Mozilla Daily Build Team - [http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) lucid main

#### Opera - [http://www.opera.com/](http://www.opera.com/)
## Run this command: sudo wget -O - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add -
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) lenny non-free

#### SMPlayer - [http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E4A4F4F4
deb [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) karmic main

#### Terminator - [http://www.tenshu.net/terminator/](http://www.tenshu.net/terminator/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1BD3A65C
deb [http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu](http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu) lucid main 

#### Themes for GNOME and Ubuntu - [https://edge.launchpad.net/~bisigi/+archive/ppa](https://edge.launchpad.net/~bisigi/+archive/ppa)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 881574DE
deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) lucid main 

#### Ubuntu Tweak - [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) lucid main


####### 3rd Party Source Repos

#### Breathe Icon Set (Source) - [https://edge.launchpad.net/~breathe-dev/+archive/ppa](https://edge.launchpad.net/~breathe-dev/+archive/ppa)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 45FFBBBA
deb-src [http://ppa.launchpad.net/breathe-dev/ppa/ubuntu](http://ppa.launchpad.net/breathe-dev/ppa/ubuntu) lucid main

#### Medibuntu (Source) - [http://www.medibuntu.org/](http://www.medibuntu.org/) 
## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free 

#### Mozilla Daily Build Team (Source) - [http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) lucid main

#### SMPlayer (Source) - [http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E4A4F4F4
deb-src [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) lucid main

#### Terminator (Source) - [http://www.tenshu.net/terminator/](http://www.tenshu.net/terminator/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1BD3A65C
deb-src [http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu](http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu) lucid main 

#### Themes for GNOME and Ubuntu (Source) - [https://edge.launchpad.net/~bisigi/+archive/ppa](https://edge.launchpad.net/~bisigi/+archive/ppa)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 881574DE
deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) lucid main

#### Ubuntu Tweak (Source) - [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) lucid main

---

### Post by sports fan Matt on 2010-06-03
I created a file for my commands and got the keys but when I try and execute this script Download this script: [http://dl.getdropbox.com/u/1115768/l...-update.tar.gz](http://dl.getdropbox.com/u/1115768/l...-update.tar.gz) it 404's.  Anyone know of another script like it?

---

### Post by sports fan Matt on 2010-06-03
Can someone help me in what to un comment so all my sources will show up?

---

