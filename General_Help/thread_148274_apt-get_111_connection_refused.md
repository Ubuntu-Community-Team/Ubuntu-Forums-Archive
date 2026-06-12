---
title: "apt-get 111 connection refused"
date: 2006-03-21
forum: General Help
---

### Post by njzillest on 2006-03-21
i cant apt-get or use synaptic because everytime i try to connect i get a "couldn not connect to local host 80- (conect 111 refused)


is there something i did wrong or is it the servers? 


i did run sudo apt-get update 

and sudo apt-get upgrade

i also went into synaptic and reloaded the packages


thanks in advance :)

---

### Post by fatsamurai on 2006-03-21
Well that is strange.. because it shouldn't be connecting to localhost anyway.  Have you got a proxy of some sort installed?

Try disabling local loopback temporarily:

sudo ifconfig lo down

Does that make any difference?

---

### Post by njzillest on 2006-03-21
no no luck, it tried it it still connects to the local host 

0% [Connecting to localhost (127.0.0.1)] [Connecting to localhost (127.0.0.1)]
(sudo apt-get upgrade)


is there anything else, im not runing ona  proxy, i checked (system prefrences- network proxy)


i do recall downloadeing some proxy thing off synaptic 4 days ago, is there a way to detect wether or not im on a proxy?


thanks

---

### Post by Zeroangel on 2006-03-21
Post the content of your /etc/apt/sources.list file. Maybe there is something wrong with it.

---

### Post by njzillest on 2006-03-22
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/

## created by arniefreeadded

---

### Post by njzillest on 2006-03-22
thats my  /etc/apt/sources.list file

---

### Post by Zeroangel on 2006-03-22
Your sources file looks fine to me!

---

### Post by njzillest on 2006-03-22
hmm its working now.. thanks :)

now i have to put a password lock on my grub lol

---

### Post by kasnas01 on 2007-02-14
how did you fix the problem
I have the same one,
thanks

---

### Post by iharrold on 2008-04-09
I am having the same issue...

sudo apt-get update
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg
  Could not connect to packages.medibuntu.org:80 (87.98.242.10). - connect (111 Connection refused) [IP: 87.98.242.10 80]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release.gpg
  Could not connect to ppa.launchpad.net:80 (91.189.90.217). - connect (111 Connection refused)
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Translation-en_US
  Could not connect to ppa.launchpad.net:80 (91.189.90.217). - connect (111 Connection refused)
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Err [http://apt.wxwidgets.org](http://apt.wxwidgets.org) gutsy-wx Release.gpg
  Could not connect to apt.wxwidgets.org:80 (72.9.158.149). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg
  Could not connect to archive.ubuntu.com:80 (91.189.88.45). - connect (111 Connection refused) [IP: 91.189.88.45 80]
Err [http://apt.wxwidgets.org](http://apt.wxwidgets.org) gutsy-wx/main Translation-en_US
  Could not connect to apt.wxwidgets.org:80 (72.9.158.149). - connect (111 Connection refused)
Err [http://apt.tt-solutions.com](http://apt.tt-solutions.com) feisty Release.gpg
  Could not connect to apt.tt-solutions.com:80 (82.238.156.189). - connect (111 Connection refused)
Err [http://apt.tt-solutions.com](http://apt.tt-solutions.com) feisty/main Translation-en_US
  Could not connect to apt.tt-solutions.com:80 (82.238.156.189). - connect (111 Connection refused)
Err [http://lgp203.free.fr](http://lgp203.free.fr) gutsy Release.gpg
  Could not connect to lgp203.free.fr:80 (212.27.63.158). - connect (111 Connection refused)
Err [http://lgp203.free.fr](http://lgp203.free.fr) gutsy/universe Translation-en_US
  Could not connect to lgp203.free.fr:80 (212.27.63.158). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US[/QUOTE]

The sources list

> deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties
deb [http://apt.mediatomb.cc/](http://apt.mediatomb.cc/) feisty main 

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# wxWidgets/wxPython repository at apt.wxwidgets.org
deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) gutsy-wx main
deb-src [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) gutsy-wx main
deb [http://apt.tt-solutions.com/ubuntu/](http://apt.tt-solutions.com/ubuntu/) feisty main

deb [http://lgp203.free.fr/ubuntu/](http://lgp203.free.fr/ubuntu/) gutsy universe
deb-src [http://lgp203.free.fr/ubuntu/](http://lgp203.free.fr/ubuntu/) gutsy universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
deb [http://lgp203.free.fr/ubuntu/](http://lgp203.free.fr/ubuntu/) gutsy universe
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) gutsy main

Anyone have any idea?  I am behind a proxy.  And I configured the network proxy with *System* > *Preferences* > *Network Proxy* and pressed the "Manual proxy configuration", checked the "Use the same proxy for all protocols".  Put the proxy address in and the port and under "Details" used my authentication account.  Also Firefox is able to get past the proxy.

EDIT:
Following this link, resolved my issues:
[http://ubuntuforums.org/showthread.php?t=83401](http://ubuntuforums.org/showthread.php?t=83401)

---

