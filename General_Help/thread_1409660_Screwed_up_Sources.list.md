---
title: "Screwed up Sources.list"
date: 2010-02-17
forum: General Help
---

### Post by Elfo33 on 2010-02-17
So, I ran an apt-get update, and got these error messages:

```
Err http://us.archive.ubuntu.com karmic/main Packages
  404  Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com karmic/restricted Packages
  404  Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com karmic/universe Packages
  404  Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com karmic/multiverse Packages
  404  Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com karmic-updates/main Packages
  404  Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com karmic-updates/restricted Packages
  404  Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com karmic-updates/universe Packages
  404  Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com karmic-updates/multiverse Packages
  404  Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com karmic-security/main Packages
  404  Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com karmic-security/restricted Packages
  404  Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com karmic-security/universe Packages
  404  Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com karmic-security/multiverse Packages
  404  Not Found [IP: 91.189.88.45 80]
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-lpia/Packages.gz  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-lpia/Packages.gz  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-lpia/Packages.gz  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-lpia/Packages.gz  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-lpia/Packages.gz  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-lpia/Packages.gz  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-lpia/Packages.gz  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-lpia/Packages.gz  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/main/binary-lpia/Packages.gz  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-lpia/Packages.gz  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-lpia/Packages.gz  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-lpia/Packages.gz  404  Not Found [IP: 91.189.88.45 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Seeing as I'm using an lpia install (not UNR), it puzzled me that it was trying to fetch from the US.  So, I looked at my sources.list and got this:

```
# deb http://ports.ubuntu.com/ubuntu-ports/ karmic main restricted
# deb http://ports.ubuntu.com/ubuntu-ports/ karmic-updates main restricted
# deb http://security.ubuntu.com/ubuntu karmic-security main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to # deb http://ports.ubuntu.com/ubuntu-ports/ karmic main restricted
# deb http://ports.ubuntu.com/ubuntu-ports/ karmic-updates main restricted
# deb http://security.ubuntu.com/ubuntu karmic-security main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ports.ubuntu.com/ubuntu-ports/ karmic-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb-src http://us.archive.ubuntu.# deb http://ports.ubuntu.com/ubuntu-ports/ karmic main restricted
# deb http://ports.ubuntu.com/ubuntu-ports/ karmic-updates main restricted
# deb http://security.ubuntu.com/ubuntu karmic-security main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ports.ubuntu.com/ubuntu-ports/ karmic-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security multiversecom/ubuntu/ karmic-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security multiverse
## your rights to use the softwar# deb http://ports.ubuntu.com/ubuntu-ports/ karmic main restricted
# deb http://ports.ubuntu.com/ubuntu-ports/ karmic-updates main restricted
# deb http://security.ubuntu.com/ubuntu karmic-security main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ports.ubuntu.com/ubuntu-ports/ karmic-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security multiversee. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ports.ubuntu.com/ubuntu-ports/ karmic-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.# deb http://ports.ubuntu.com/ubuntu-ports/ karmic main restricted
# deb http://ports.ubuntu.com/ubuntu-ports/ karmic-updates main restricted
# deb http://security.ubuntu.com/ubuntu karmic-security main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ports.ubuntu.com/ubuntu-ports/ karmic-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security multiverse
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security multiverse
```

I don't know what repository I'm supposed to be using, my recollection is that it's a port in Britian.  Anyways, Administration > Software Sources refuses to allow me to pick a different server, as it complains there is no internet connection; which is bunk.

So, does anyone know either what repository to use, how to fix this, or can please post a copy of their sources.list for lpia architecture?

---

### Post by Satoru-san on 2010-02-17
[s]Those links resolve for me. Try restarting your comptuer (yes I know there are other ways) but this is easiest. 

Try again after reboot.[/s]

that wont fix it.

---

### Post by Elfo33 on 2010-02-17
Already tried rebooting, as well as checking sources.list.save

Ubuntu doesn't have the lpia packages in the main repository, so it looks like somewhere along the line my machine got confused between i386 and lpia.  I want to use lpia.

I'd reinstall, except this is a netbook so no disc drive.  Can't install usb-creator because it's the wrong architecture and refuses to install.

---

