---
title: "audacity install and 'fix broken package first'"
date: 2011-10-01
forum: General Help
---

### Post by yumgnomeandthensome on 2011-10-01
Hi, 
I've never had trouble with installing audacity, but i've upgraded to natty from 10.10 and my source.list might be a little stuffed.
if its as easy as ensuring I have the right deb link in my source list can someone include which link I should edit my source.list with and if there are any other things to note.

Error I get is :
The following packages have unmet dependencies:
 audacity : Depends: audacity-data (= 1.3.13+svn20110930+r6868-0~natty1) but it is not going to be installed
E: Broken packages

I have removed my audacity-data and reinstalled it, but still get error

---

### Post by oldos2er on 2011-10-01
Can you post the output from both these commands? ```
cat /etc/apt/sources.list

ls /etc/apt/sources.list.d/
```

---

### Post by yumgnomeandthensome on 2011-10-01
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) natty main universe multiverse restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) natty main universe multiverse restricted

###### Ubuntu Update Repos
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) natty-security main universe multiverse restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) natty-updates main universe multiverse restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) natty-security main universe multiverse restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) natty-updates main universe multiverse restricted

###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### Audacity - [http://audacity.sourceforge.net/](http://audacity.sourceforge.net/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys     1024R/BB901940
deb [http://ppa.launchpad.net/audacity-team/daily/ubuntu](http://ppa.launchpad.net/audacity-team/daily/ubuntu) natty main

#### AWN (Avant Window Navigator) Testing Packages - [http://awn-project.org/](http://awn-project.org/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BF810CD5
deb [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu) natty main

#### Banshee - [https://edge.launchpad.net/~banshee-team](https://edge.launchpad.net/~banshee-team)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7
deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) natty main

#### Chromium Project - [http://code.google.com/chromium/](http://code.google.com/chromium/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E5E17B5
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) natty main

#### DeaDBeeF - [http://deadbeef.sourceforge.net/](http://deadbeef.sourceforge.net/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3C8E2A7F
deb [http://ppa.launchpad.net/alexey-smirnov/deadbeef/ubuntu](http://ppa.launchpad.net/alexey-smirnov/deadbeef/ubuntu) natty main

#### Deluge BitTorrent - [http://www.deluge-torrent.org/](http://www.deluge-torrent.org/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 249AD24C
deb [http://ppa.launchpad.net/deluge-team/ppa/ubuntu](http://ppa.launchpad.net/deluge-team/ppa/ubuntu) natty main

#### Esmska - [http://code.google.com/p/esmska/](http://code.google.com/p/esmska/) 
## Run this command: wget -q -O - [http://repo.palatinus.cz/repo.key](http://repo.palatinus.cz/repo.key) | sudo apt-key add -
deb [http://repo.palatinus.cz/stable](http://repo.palatinus.cz/stable) /

#### FBReader - [http://www.fbreader.org/desktop/](http://www.fbreader.org/desktop/)
## Run this command: [http://www.fbreader.org/desktop/debian/geometer.fbreader.org.asc](http://www.fbreader.org/desktop/debian/geometer.fbreader.org.asc) -O- | sudo apt-key add -
deb [http://www.fbreader.org/desktop/debian](http://www.fbreader.org/desktop/debian) stable main

#### Flacon - [http://kde-apps.org/content/show.php?content=113388](http://kde-apps.org/content/show.php?content=113388)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F2A61FE5
deb [http://ppa.launchpad.net/flacon/ppa/ubuntu](http://ppa.launchpad.net/flacon/ppa/ubuntu) natty main

#### GCstar - [http://www.gcstar.org/](http://www.gcstar.org/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5BE6AD9A
deb [http://ppa.launchpad.net/gcstar/gcstar-dev/ubuntu](http://ppa.launchpad.net/gcstar/gcstar-dev/ubuntu) natty main

#### GetDeb - [http://www.getdeb.net](http://www.getdeb.net)
## Run this command: wget -q -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) natty-getdeb apps

#### Glx-Dock / Cairo-Dock - [http://www.glx-dock.org](http://www.glx-dock.org)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E80D6BF5
deb [http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu](http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu) natty main

#### GNUzilla and IceCat - [http://www.gnu.org/software/gnuzilla/](http://www.gnu.org/software/gnuzilla/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 
deb [http://ppa.launchpad.net/gnuzilla-team/ppa/ubuntu](http://ppa.launchpad.net/gnuzilla-team/ppa/ubuntu) natty main

#### Google Linux Software Repositories - [http://www.google.com/linuxrepositories/](http://www.google.com/linuxrepositories/)
## Run this command: wget -q [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) -O- | sudo apt-key add -
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

#### Google Linux Software Repositories (Testing) - [http://www.google.com/linuxrepositories/](http://www.google.com/linuxrepositories/)
## Run this command: wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | sudo apt-key add  -
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing non-free

#### Gwibber (Daily) - [https://launchpad.net/gwibber](https://launchpad.net/gwibber)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 72D340A3
deb [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu) natty main

#### LibreOffice 3.3 - [http://www.documentfoundation.org/download/](http://www.documentfoundation.org/download/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
deb [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) natty main

#### Miro HD Video Player - [http://www.getmiro.com/](http://www.getmiro.com/)
## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2D75E850
deb [http://ppa.launchpad.net/pcf/miro-releases/ubuntu](http://ppa.launchpad.net/pcf/miro-releases/ubuntu) natty main


####### 3rd Party Source Repos

#### Audacity (Source) - [http://audacity.sourceforge.net/](http://audacity.sourceforge.net/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys     1024R/BB901940
deb-src [http://ppa.launchpad.net/audacity-team/daily/ubuntu](http://ppa.launchpad.net/audacity-team/daily/ubuntu) natty main

#### AWN (Avant Window Navigator) Testing Packages (Source) - [http://awn-project.org/](http://awn-project.org/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BF810CD5
deb-src [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu) natty main

#### Banshee (Source) - [https://edge.launchpad.net/~banshee-team](https://edge.launchpad.net/~banshee-team)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7
deb-src [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) natty main

#### Chromium Project (Source) - [http://code.google.com/chromium/](http://code.google.com/chromium/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E5E17B5
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) natty main

#### DeaDBeeF (Source) - [http://deadbeef.sourceforge.net/](http://deadbeef.sourceforge.net/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3C8E2A7F
deb-src [http://ppa.launchpad.net/alexey-smirnov/deadbeef/ubuntu](http://ppa.launchpad.net/alexey-smirnov/deadbeef/ubuntu) natty main

#### Deluge BitTorrent (Source) - [http://www.deluge-torrent.org/](http://www.deluge-torrent.org/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 249AD24C
deb-src [http://ppa.launchpad.net/deluge-team/ppa/ubuntu](http://ppa.launchpad.net/deluge-team/ppa/ubuntu) natty main

#### FBReader (Source) - [http://www.fbreader.org/desktop/](http://www.fbreader.org/desktop/)
## Run this command: [http://www.fbreader.org/desktop/debian/geometer.fbreader.org.asc](http://www.fbreader.org/desktop/debian/geometer.fbreader.org.asc) -O- | sudo apt-key add -
deb-src [http://www.fbreader.org/desktop/debian](http://www.fbreader.org/desktop/debian) stable main

#### Flacon (Source) - [http://kde-apps.org/content/show.php?content=113388](http://kde-apps.org/content/show.php?content=113388)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F2A61FE5
deb-src [http://ppa.launchpad.net/flacon/ppa/ubuntu](http://ppa.launchpad.net/flacon/ppa/ubuntu) natty main

#### GCstar (Source) - [http://www.gcstar.org/](http://www.gcstar.org/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5BE6AD9A
deb-src [http://ppa.launchpad.net/gcstar/gcstar-dev/ubuntu](http://ppa.launchpad.net/gcstar/gcstar-dev/ubuntu) natty main

#### Glx-Dock / Cairo-Dock (Source) - [http://www.glx-dock.org](http://www.glx-dock.org)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E80D6BF5
deb-src [http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu](http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu) natty main

#### GNUzilla and IceCat (Source) - [http://www.gnu.org/software/gnuzilla/](http://www.gnu.org/software/gnuzilla/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 
deb-src [http://ppa.launchpad.net/gnuzilla-team/ppa/ubuntu](http://ppa.launchpad.net/gnuzilla-team/ppa/ubuntu) natty main

#### Gwibber (Daily) (Source) - [https://launchpad.net/gwibber](https://launchpad.net/gwibber)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 72D340A3
deb-src [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu) natty main

#### LibreOffice 3.3 (Source) - [http://www.documentfoundation.org/download/](http://www.documentfoundation.org/download/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
deb-src [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) natty main

#### Miro HD Video Player (Source) - [http://www.getmiro.com/](http://www.getmiro.com/)
## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2D75E850
deb-src [http://ppa.launchpad.net/pcf/miro-releases/ubuntu](http://ppa.launchpad.net/pcf/miro-releases/ubuntu) natty main
deb [http://ubuntu.mirror.cambrium.nl/ubuntu/pool/universe/a/audacity](http://ubuntu.mirror.cambrium.nl/ubuntu/pool/universe/a/audacity) natty main universe

***************************************************

am-monkeyd-nautilus-elementary-ppa-natty.list
am-monkeyd-nautilus-elementary-ppa-natty.list.save
atareao-atareao-natty.list
atareao-atareao-natty.list.save
google-chrome.list
google-chrome.list.save
google-talkplugin.list
google-talkplugin.list.save
indicator-multiload-daily-natty.list
indicator-multiload-daily-natty.list.save
lorenzo-carbonell-atareao-natty.list
lorenzo-carbonell-atareao-natty.list.save
ubuntu-tweak-testing-ppa-natty.list
ubuntu-tweak-testing-ppa-natty.list.save

---

### Post by oldos2er on 2011-10-01
That's an awful lot of PPAs.

Open Synaptic Package Manager, click Edit, Fix Broken Packages, then see if it will let you update.

---

### Post by yumgnomeandthensome on 2011-10-01
yeah I think its cos I upgraded directly from 10.10 to 11.04, 
ie not a fresh install. SO it hashes out ones that are no longer needed:

E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

---

