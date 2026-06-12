---
title: "apt-get ¦ aptitude ¦ synaptic error"
date: 2010-04-19
forum: General Help
---

### Post by l4zy on 2010-04-19
Hi,

I'm having problems with apt-get / aptitude / synaptic.

When i run apt-get update or upgrade error i get following error message:

Reading package lists... Error!
E: Unable to seek to 18446744071846088703
W: Unable to munmap
E: The package lists or status file could not be parsed or opened.


I've runned apt-get clean cmd, but it didn't help. Pc is pretty new with 8 GB ram ect.

Synaptic and aptitude gives this error when you open those.


Any ideas about this problem.

---

### Post by l4zy on 2010-04-19
Got the first problem fixer by increasing apt-cache size. 
But now i'm facing new problem:

[SIZE="1"]apt-get update
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) karmic Release.gpg
  Could not resolve 'http'
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) karmic/main Translation-en_US
  Could not resolve 'http'
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) karmic/restricted Translation-en_US
  Could not resolve 'http'
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) karmic/universe Translation-en_US
  Could not resolve 'http'
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) karmic/multiverse Translation-en_US
  Could not resolve 'http'
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) karmic-updates Release.gpg
  Could not resolve 'http'
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) karmic-updates/main Translation-en_US
  Could not resolve 'http'
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
  Could not resolve 'http'
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) karmic-updates/universe Translation-en_US
  Could not resolve 'http'
Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
  Could not resolve 'http'
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg
  Could not resolve 'http'
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US
  Could not resolve 'http'
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg
  Could not resolve 'http'
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US
  Could not resolve 'http'
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg
  Could not resolve 'http'
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US
  Could not resolve 'http'
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                            
  Could not resolve 'http'
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US                 
  Could not resolve 'http'
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
  Could not resolve 'http'
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
  Could not resolve 'http'
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
  Could not resolve 'http'
Err [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic Release.gpg                
  Could not resolve 'http'
Err [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Translation-en_US     
  Could not resolve 'http'
Err [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg              
  Could not resolve 'http'
Err [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US
  Could not resolve 'http'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg
  Could not resolve 'http'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
  Could not resolve 'http'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
  Could not resolve 'http'
Reading package lists... Done
W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://fi.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not resolve 'http'

W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2](http://fi.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2)  Could not resolve 'http'

W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2](http://fi.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'http'

W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2](http://fi.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2)  Could not resolve 'http'

W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2](http://fi.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'http'

W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://fi.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Could not resolve 'http'

W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2](http://fi.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'http'

W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2](http://fi.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'http'

W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2](http://fi.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'http'

W: Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2](http://fi.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'http'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  Could not resolve 'http'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'http'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'http'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'http'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'http'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg](http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg)  Could not resolve 'http'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_US.bz2)  Could not resolve 'http'

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/Release.gpg](http://packages.medibuntu.org/dists/hardy/Release.gpg)  Could not resolve 'http'

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/hardy/free/i18n/Translation-en_US.bz2)  Could not resolve 'http'

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/non-free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/hardy/non-free/i18n/Translation-en_US.bz2)  Could not resolve 'http'

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/karmic/Release.gpg](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/karmic/Release.gpg)  Could not resolve 'http'

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2)  Could not resolve 'http'

W: Failed to fetch [http://deb.playonlinux.com/dists/karmic/Release.gpg](http://deb.playonlinux.com/dists/karmic/Release.gpg)  Could not resolve 'http'

W: Failed to fetch [http://deb.playonlinux.com/dists/karmic/main/i18n/Translation-en_US.bz2](http://deb.playonlinux.com/dists/karmic/main/i18n/Translation-en_US.bz2)  Could not resolve 'http'

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/karmic/Release.gpg](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/karmic/Release.gpg)  Could not resolve 'http'

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2)  Could not resolve 'http'

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/karmic/Release.gpg](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/karmic/Release.gpg)  Could not resolve 'http'

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2)  Could not resolve 'http'

W: Some index files failed to download, they have been ignored, or old ones used instead.
[/SIZE]

And here is the /etc/apt/sources.list file: 

[SIZE="1"]cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
[/SIZE]

All other traffic to the internet works. So no problems with dns or anything.

---

### Post by l4zy on 2010-04-19
Solved:

Solution rebooted. Some dns-failure with apt.

---

