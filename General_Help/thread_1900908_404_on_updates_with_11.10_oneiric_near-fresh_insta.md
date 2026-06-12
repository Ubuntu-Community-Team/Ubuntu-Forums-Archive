---
title: "404 on updates with 11.10 oneiric near-fresh install"
date: 2011-12-27
forum: General Help
---

### Post by h6w on 2011-12-27
For the past couple of days (possibly a week), the update of sources has failed with 404 errors.  This is on an 11.10 oneiric fresh install on an amd64 machine.

I have checked and compressed versions of these files exist, but not uncompressed.

The errors look like:
```
W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/source/Sources  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.88.45 80]

```

The sources list looks like:
```
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://ca.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
```

---

### Post by TeoBigusGeekus on 2011-12-27
Have you tried changing your server?

---

### Post by h6w on 2011-12-29
Well, it appears to have been fixed upstream this morning.   Oh well....

---

