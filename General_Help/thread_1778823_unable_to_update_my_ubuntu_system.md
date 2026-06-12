---
title: "unable to update my ubuntu system"
date: 2011-06-09
forum: General Help
---

### Post by mo.mughrabi on 2011-06-09
hi, am new to ubuntu and recently installed it on my laptop. I come from a debian background so i have a little idea

once the installation is completed, am trying to update and/or add remove programs but am getting an error saying 

```
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
```

when i try to run 

sudo apt-get update

i get the following error

```
mo@ubuntu:~$ sudo apt-get update
Ign http://us.archive.ubuntu.com intrepid Release.gpg
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US
Ign http://security.ubuntu.com intrepid-security Release.gpg
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates Release.gpg
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com intrepid Release
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US
Ign http://security.ubuntu.com intrepid-security Release
Ign http://us.archive.ubuntu.com intrepid-updates Release
Ign http://security.ubuntu.com intrepid-security/main Packages
Ign http://us.archive.ubuntu.com intrepid/main Packages
Ign http://us.archive.ubuntu.com intrepid/restricted Packages
Ign http://us.archive.ubuntu.com intrepid/main Sources
Ign http://us.archive.ubuntu.com intrepid/restricted Sources
Ign http://us.archive.ubuntu.com intrepid/universe Packages
Ign http://us.archive.ubuntu.com intrepid/universe Sources
Ign http://us.archive.ubuntu.com intrepid/multiverse Packages
Ign http://security.ubuntu.com intrepid-security/restricted Packages
Ign http://security.ubuntu.com intrepid-security/main Sources
Ign http://security.ubuntu.com intrepid-security/restricted Sources
Ign http://security.ubuntu.com intrepid-security/universe Packages
Ign http://security.ubuntu.com intrepid-security/universe Sources
Ign http://security.ubuntu.com intrepid-security/multiverse Packages
Ign http://us.archive.ubuntu.com intrepid/multiverse Sources
Ign http://us.archive.ubuntu.com intrepid-updates/main Packages
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Packages
Ign http://us.archive.ubuntu.com intrepid-updates/main Sources
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Sources
Ign http://us.archive.ubuntu.com intrepid-updates/universe Packages
Ign http://us.archive.ubuntu.com intrepid-updates/universe Sources
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Packages
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Sources
Err http://us.archive.ubuntu.com intrepid/main Packages
  404 Not Found [IP: 91.189.92.171 80]
Ign http://security.ubuntu.com intrepid-security/multiverse Sources
Err http://security.ubuntu.com intrepid-security/main Packages
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com intrepid-security/restricted Packages
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com intrepid-security/main Sources
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com intrepid-security/restricted Sources
  404 Not Found [IP: 91.189.92.167 80]
Err http://us.archive.ubuntu.com intrepid/restricted Packages
  404 Not Found [IP: 91.189.92.171 80]
Err http://us.archive.ubuntu.com intrepid/main Sources
  404 Not Found [IP: 91.189.92.171 80]
Err http://us.archive.ubuntu.com intrepid/restricted Sources
  404 Not Found [IP: 91.189.92.171 80]
Err http://us.archive.ubuntu.com intrepid/universe Packages
  404 Not Found [IP: 91.189.92.171 80]
Err http://us.archive.ubuntu.com intrepid/universe Sources
  404 Not Found [IP: 91.189.92.171 80]
Err http://us.archive.ubuntu.com intrepid/multiverse Packages
  404 Not Found [IP: 91.189.92.171 80]
Err http://us.archive.ubuntu.com intrepid/multiverse Sources
  404 Not Found [IP: 91.189.92.171 80]
Err http://us.archive.ubuntu.com intrepid-updates/main Packages
  404 Not Found [IP: 91.189.92.171 80]
Err http://us.archive.ubuntu.com intrepid-updates/restricted Packages
  404 Not Found [IP: 91.189.92.171 80]
Err http://us.archive.ubuntu.com intrepid-updates/main Sources
  404 Not Found [IP: 91.189.92.171 80]
Err http://security.ubuntu.com intrepid-security/universe Packages
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com intrepid-security/universe Sources
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com intrepid-security/multiverse Packages
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com intrepid-security/multiverse Sources
  404 Not Found [IP: 91.189.92.167 80]
Err http://us.archive.ubuntu.com intrepid-updates/restricted Sources
  404 Not Found [IP: 91.189.92.171 80]
Err http://us.archive.ubuntu.com intrepid-updates/universe Packages
  404 Not Found [IP: 91.189.92.171 80]
Err http://us.archive.ubuntu.com intrepid-updates/universe Sources
  404 Not Found [IP: 91.189.92.171 80]
Err http://us.archive.ubuntu.com intrepid-updates/multiverse Packages
  404 Not Found [IP: 91.189.92.171 80]
Err http://us.archive.ubuntu.com intrepid-updates/multiverse Sources
  404 Not Found [IP: 91.189.92.171 80]
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.92.167 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

```


although i never touched my apt sources, they are as is from the installation, here is the file

```

mo@ubuntu:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

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

```

any one can advise?

---

### Post by drs305 on 2011-06-09
Intrepid reached End of Life (EOL) at the end of April, so it's repository is no longer available at the original site.

If you intend on sticking with Intrepid, you can change your repository server to "http://old-releases.ubuntu.com/" so you can still install packages. 

You can alter your current sources.list (make a backup) by running this search/replace:

Find: [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)
Replace with: [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu)



The old-releases repository is not updated, but does provide the repository as it existed when Intrepid reached EOL.

It's probably time to consider upgrading!

---

### Post by mo.mughrabi on 2011-06-09
Can you please advise on how i can upgrade? do you mean by upgrading remove my current ubuntu installation and get a fresh copy?

---

### Post by drs305 on 2011-06-09
I think even though Intrepid is EOL you may still be able to do an online upgrade to 10.04 from 9.10, or you can do a clean installation using a LiveCD. (See the link at the end of this post.)

If you don't already have a separate /home partition (and/or don't want to make one), doing an online upgrade will allow you to keep many of your current settings and customizations. You can upgrade to 10.04 in this manner.

If you decide to install from the CD, you can either install the new release in the same partition as you have Intrepid. In this case, your system will be erased and none of your settings will be saved (unless you have a separate /home partition). If you do a clean installation, you can install any of the following currently-supported releases: Lucid, Maverick, Natty.

Here is a link on upgrading:
[https://help.ubuntu.com/community/UpgradeNotes]("https://help.ubuntu.com/community/UpgradeNotes")

---

