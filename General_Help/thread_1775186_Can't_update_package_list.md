---
title: "Can't update package list"
date: 2011-06-04
forum: General Help
---

### Post by dgel on 2011-06-04
Hi,

For the last 10 days, whenever I try to update my packages, it fails with the following error messages:

```
Err http://canonical.ubuntu.com natty/partner Sources         
  Something wicked happened resolving 'canonical.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://canonical.ubuntu.com natty/partner amd64 Packages
  Something wicked happened resolving 'canonical.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://canonical.ubuntu.com natty/partner Translation-en_GB
  Something wicked happened resolving 'canonical.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://canonical.ubuntu.com natty/partner Translation-en
  Something wicked happened resolving 'canonical.ubuntu.com:http' (-5 - No address associated with hostname)
W: Failed to fetch http://canonical.ubuntu.com/ubuntu/dists/natty/Release.gpg  Something wicked happened resolving 'canonical.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://canonical.ubuntu.com/ubuntu/dists/natty/partner/source/Sources  Something wicked happened resolving 'canonical.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://canonical.ubuntu.com/ubuntu/dists/natty/partner/binary-amd64/Packages  Something wicked happened resolving 'canonical.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://canonical.ubuntu.com/ubuntu/dists/natty/partner/i18n/Translation-en_GB  Something wicked happened resolving 'canonical.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://canonical.ubuntu.com/ubuntu/dists/natty/partner/i18n/Translation-en  Something wicked happened resolving 'canonical.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Anyone have any idea what might cause this? everything else seems to be working fine..

---

### Post by ivanovnegro on 2011-06-04
Can you post here your sources list with typing this in the terminal:

```
sudo cat /etc/apt/sources.list
```

---

### Post by brolin_1911a1 on 2011-08-11
I'm having the same problem and getting the same error message.

Here's my sources.list cut-and-pasted from gedit:

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty restricted universe main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty restricted universe main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates restricted universe main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates restricted universe main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports restricted multiverse universe main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security restricted universe main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security restricted universe main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) natty-getdeb apps
# deb-src [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) natty-getdeb apps
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) natty-getdeb games
deb-src [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) natty-getdeb games
deb [http://canonical.ubuntu.com/ubuntu](http://canonical.ubuntu.com/ubuntu) natty partner
deb-src [http://canonical.ubuntu.com/ubuntu](http://canonical.ubuntu.com/ubuntu) natty partner
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free

---

### Post by plucky on 2011-08-11
> deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner


Remove the quoted lines from your sources.list and put a # in front of all the lines that start with "**deb-src**" then run ```
sudo apt-get update
``` and see what happens.

Post the output if there are any errors.

Good Luck

---

