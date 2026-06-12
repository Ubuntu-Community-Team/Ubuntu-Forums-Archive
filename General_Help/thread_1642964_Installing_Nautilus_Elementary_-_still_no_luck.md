---
title: "Installing Nautilus Elementary - still no luck"
date: 2010-12-11
forum: General Help
---

### Post by Belgatom on 2010-12-11
At first I was behind a firewall and was having problems getting to the keyserver. Now that's been resolved, I'm still not getting where I want to go. Can someone help me? And if possible, I would appreciate some tech feedback to teach me what actually is going wrong. 

(Give a man a  fish <> Teach a man to fish)

```
sudo add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa[sudo] password for belgatom: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 91DB0C47720C152FF466E7BA61E091672E206FF0
gpg: requesting key 2E206FF0 from hkp server keyserver.ubuntu.com
gpg: key 2E206FF0: public key "Launchpad nautilus-elementary" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
belgatom@Nerum:~$ sudo apt-get update && sudo apt-get dist-upgrade
E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-maverick.list
E: The list of sources could not be read.
```

---

### Post by gandaran on 2010-12-11
> E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-maverick.list
E: The list of sources could not be read.
post the content of the sources list, seams there is a problem with one line
```
sudo gedit /etc/apt/sources.list
```

---

### Post by Belgatom on 2010-12-11
```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu maverick main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu maverick-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu maverick universe
deb-src http://archive.ubuntu.com/ubuntu maverick universe
deb http://archive.ubuntu.com/ubuntu maverick-updates universe
deb-src http://archive.ubuntu.com/ubuntu maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu maverick multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick multiverse
deb http://archive.ubuntu.com/ubuntu maverick-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://be.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://be.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://archive.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-security main restricted
deb http://archive.ubuntu.com/ubuntu maverick-security universe
deb-src http://archive.ubuntu.com/ubuntu maverick-security universe
deb http://archive.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick-security multiverse
```

---

### Post by plucky on 2010-12-11
It is a PPA which should be in /etc/apt/sources.list.d/ 

Try ```
cat /etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-maverick.list
``` and post output.

To edit that file ```
gksudo gedit /etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-maverick.list
```

Good Luck

---

### Post by Belgatom on 2010-12-11
Rock and Roll. Thx, worked a dream.

---

