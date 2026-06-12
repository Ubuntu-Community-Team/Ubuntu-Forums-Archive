---
title: "Error authenticating some packages"
date: 2010-10-20
forum: General Help
---

### Post by naveedmurtuza on 2010-10-20
Hi everyone

i got this error today when trying to update.
output of apt-get update
```

W: GPG error: http://archive.ubuntu.com lucid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://archive.ubuntu.com lucid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-amd64/Packages.bz2  Hash Sum mismatch

W: Failed to fetch http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.bz2  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

i tried to install to gpg keys but it gave me this error

```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40976EAF437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1


```


and here is the contents of sources.list
```

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu lucid universe
deb-src http://archive.ubuntu.com/ubuntu lucid universe
deb http://archive.ubuntu.com/ubuntu lucid-updates universe
deb-src http://archive.ubuntu.com/ubuntu lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu lucid multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid multiverse
deb http://archive.ubuntu.com/ubuntu lucid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://sa.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://sa.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://archive.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid-security main restricted
deb http://archive.ubuntu.com/ubuntu lucid-security universe
deb-src http://archive.ubuntu.com/ubuntu lucid-security universe
deb http://archive.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-security multiverse

# Google software repository
deb http://dl.google.com/linux/deb/ stable non-free main
deb http://packages.medibuntu.org/ lucid free non-free
deb-src http://packages.medibuntu.org/ lucid free non-free

```

 i have also tried changing the servers as suggested in one of the threads.. but could nt fix it...

also attaching the screenshot of update manager..

any solutions??

---

### Post by naveedmurtuza on 2010-10-21
anyone please?? solution to fix it.

---

### Post by plucky on 2010-10-21
Open a terminal and post output of ```
sudo apt-get update
```
If no errors then try ```
sudo apt-get upgrade
``` to actually install the upgrades found in the previous command.

> W: Failed to fetch [http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.bz2](http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.bz2)  Hash Sum mismatch



Did the error change when you changed servers?
That is usually a problem when then servers haven't synced with the main server.

Open Software Sources and on the Other Software tab,un-tick all the PPA sources and Google sources then close.

It will ask to reload.Do so.

Post any errors.

Good Luck

---

