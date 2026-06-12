---
title: "apt-get install xorg-driver-fglrx +returns 403 forbidden"
date: 2010-01-21
forum: General Help
---

### Post by srinivas2828 on 2010-01-21
I am trying to install xorg-driver-fglrx using apt--get but it return error which says btw i am using ubuntu8.10 Desktop distribution
```

root@VAIO:/home/miriyala# apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms fakeroot fglrx-amdcccle fglrx-kernel-source
Suggested packages:
  libamdxvba1
The following NEW packages will be installed:
  dkms fakeroot fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx
0 upgraded, 5 newly installed, 0 to remove and 339 not upgraded.
Need to get 20.2MB of archives.
After this operation, 56.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  dkms fakeroot fglrx-kernel-source xorg-driver-fglrx fglrx-amdcccle
Install these packages without verification [y/N]? y
Err http://in.archive.ubuntu.com intrepid-updates/main dkms 2.0.20.4-0ubuntu2.1
  403 Forbidden
Err http://in.archive.ubuntu.com intrepid-updates/main fakeroot 1.9.5ubuntu1.1
  403 Forbidden
Err http://in.archive.ubuntu.com intrepid-updates/restricted fglrx-kernel-source 2:8.543-0ubuntu4.1
  403 Forbidden
Err http://security.ubuntu.com intrepid-security/restricted fglrx-kernel-source 2:8.543-0ubuntu4.1
  403 Forbidden
Err http://security.ubuntu.com intrepid-security/restricted xorg-driver-fglrx 2:8.543-0ubuntu4.1
  403 Forbidden
Err http://security.ubuntu.com intrepid-security/restricted fglrx-amdcccle 2:8.543-0ubuntu4.1
  403 Forbidden
Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.0.20.4-0ubuntu2.1_all.deb  403 Forbidden
Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/f/fakeroot/fakeroot_1.9.5ubuntu1.1_i386.deb  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer/fglrx-kernel-source_8.543-0ubuntu4.1_i386.deb  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer/xorg-driver-fglrx_8.543-0ubuntu4.1_i386.deb  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer/fglrx-amdcccle_8.543-0ubuntu4.1_i386.deb  403 Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


```/etc/apt/sources.list contains
```

#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://in.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://in.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://in.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://in.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://in.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse

# wxWidgets/wxPython repository at apt.wxwidgets.org
    deb http://apt.wxwidgets.org/ intrepid-wx main
    deb-src http://apt.wxwidgets.org/ intrepid-wx main  


```any idea?

---

### Post by dcstar on 2010-01-21
> **srinivas2828 said:**
> I am trying to install xorg-driver-fglrx using apt--get but it return error which says btw i am using ubuntu8.10 Desktop distribution
```

........
Err http://in.archive.ubuntu.com intrepid-updates/main dkms 2.0.20.4-0ubuntu2.1
  403 Forbidden
........

```any idea?

Select a different repository.

BTW, 8.10 is only supported until April this year:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by flabdablet on 2010-01-21
Did you already try apt-get update?

That's often fixed weird non-authentication and repository access errors for me.

---

