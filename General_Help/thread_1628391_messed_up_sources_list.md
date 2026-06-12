---
title: "messed up sources list"
date: 2010-11-22
forum: General Help
---

### Post by RastaManPower on 2010-11-22
hello guys i have messed up my sources list with ubuntu tweak xD
my sources list is now blank ...ops..how dop i fix it?
i am also getting this error in synaptic when i press refresh
W: Failed to fetch [http://ppa.launchpad.net/awn-testing/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/awn-testing/ppa/ubuntu/dists/maverick/Release.gpg)  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch [http://ppa.launchpad.net/awn-testing/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/awn-testing/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Unable to connect to 192.168.0.1:8123:

W: Failed to fetch [http://ppa.launchpad.net/awn-testing/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/awn-testing/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.0.1:8123:

W: Failed to fetch [http://ppa.launchpad.net/exaile-devel/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/exaile-devel/ppa/ubuntu/dists/maverick/Release.gpg)  Unable to connect to 192.168.0.1:8123:

W: Failed to fetch [http://ppa.launchpad.net/exaile-devel/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/exaile-devel/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Unable to connect to 192.168.0.1:8123:

W: Failed to fetch [http://ppa.launchpad.net/exaile-devel/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/exaile-devel/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.0.1:8123:

W: Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/maverick/Release.gpg)  Unable to connect to 192.168.0.1:8123:

W: Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Unable to connect to 192.168.0.1:8123:

W: Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.0.1:8123:

W: Failed to fetch [http://ppa.launchpad.net/tehnick/tehnick/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/tehnick/tehnick/ubuntu/dists/maverick/Release.gpg)  Unable to connect to 192.168.0.1:8123:

W: Failed to fetch [http://ppa.launchpad.net/tehnick/tehnick/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/tehnick/tehnick/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Unable to connect to 192.168.0.1:8123:

W: Failed to fetch [http://ppa.launchpad.net/tehnick/tehnick/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/tehnick/tehnick/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.0.1:8123:

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/maverick/Release.gpg)  Unable to connect to 192.168.0.1:8123:

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Unable to connect to 192.168.0.1:8123:

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.0.1:8123:

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by RastaManPower on 2010-11-22
the basic sources list is this right?
 deb [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick main universe restricted multiverse
deb [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick-updates universe main multiverse restricted
deb [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick-proposed universe main multiverse restricted
deb [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick-security universe main multiverse restricted
deb [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick-backports main multiverse restricted universe
deb-src [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick main universe restricted multiverse
deb-src [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick-security universe main multiverse restricted
deb-src [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick-updates universe main multiverse restricted
deb-src [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick-proposed universe main multiverse restricted
deb-src [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick-backports universe main multiverse restricted
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main #Third party developers repository
_________________________________________________________________________________________
ubun tu sources list generator???? is this correct?

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main universe 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main universe 

###### Ubuntu Update Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security main universe 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main universe 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed main universe 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main universe 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security main universe 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main universe 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed main universe 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main universe 

###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BF810CD5
deb [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu) maverick main # AWN (Avant Window Navigator) Testing Packages - [http://awn-project.org/](http://awn-project.org/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E2314809
deb [http://ppa.launchpad.net/bjfs/ppa/ubuntu](http://ppa.launchpad.net/bjfs/ppa/ubuntu) maverick main # Emesene - [http://www.emesene.org](http://www.emesene.org)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) maverick main # Mozilla Daily Build Team - [http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

## Run this command: gpg --keyserver subkeys.pgp.net --recv 886DDD89 && gpg --export --armor 886DDD89 | sudo apt-key add -
deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) maverick main # Tor Project - [http://www.torproject.org/](http://www.torproject.org/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) maverick main # Ubuntu Tweak - [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

## Run this command: wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick non-free # VirtualBox - [http://www.virtualbox.org](http://www.virtualbox.org)

---

### Post by RastaManPower on 2010-11-22
i fixed the connection problem by uninstalling tor-polipo-vidalia... i will try to reinstall again. what bout the sources list? how do i fix them up?

---

