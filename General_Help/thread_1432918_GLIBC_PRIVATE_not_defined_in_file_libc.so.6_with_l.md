---
title: "GLIBC_PRIVATE not defined in file libc.so.6 with link time reference"
date: 2010-03-18
forum: General Help
---

### Post by bonfire89 on 2010-03-18
Hey there,

I'm running Ubuntu Server 9.10

The install is pretty much brand new.

and I am not able to restart the server as I receive

```
# shutdown -r now
shutdown: relocation error: shutdown: symbol __abort_msg, version GLIBC_PRIVATE not defined in file libc.so.6 with link time reference
```

when I try to do so.


here is my sources.list

```
   GNU nano 2.0.9                                                                   File: /etc/apt/sources.list                                                                                                                                             

# deb http://ca.archive.ubuntu.com/ubuntu/ karmic main restricted
# deb http://ca.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
# deb http://security.ubuntu.com/ubuntu karmic-security main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ karmic universe
deb http://ca.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse

#sabnzbd
deb http://ppa.launchpad.net/jcfp/ppa/ubuntu karmic main
```

I have tried

```
 aptitude update
aptitude upgrade
```

and

```
aptitude reinstall rsyslog -f
```

and

```
dpkg-reconfigure rsyslog
```

which resulted in

```
dpkg-reconfigure rsyslog
/usr/sbin/dpkg-reconfigure: rsyslog is broken or not fully installed
```

help on resolving this issue will be appreciated.

thanks!

---

