---
title: "Synaptic 404 error"
date: 2006-05-21
forum: General Help
---

### Post by sparky25890 on 2006-05-21
Hi, 
new to kubuntu, but not linux.

when ever i try to download new packages on Synaptic it gives me 404 errors.  Im 100% positive that it works.  After searching around a while i tried apt-get update, and it gives me more 404 errors on everything.  same thing when i try to use wget.  any ideas?



```
sudo apt-get update
Password:
Ign http://archive.ubuntu.com breezy Release.gpg
Ign http://wine.budgetdedicated.com breezy Release.gpg
Ign http://archive.ubuntu.com breezy Release
Ign http://wine.budgetdedicated.com breezy Release
Ign http://archive.ubuntu.com breezy/universe Packages
Ign http://wine.budgetdedicated.com breezy/main Packages
Err http://archive.ubuntu.com breezy/universe Packages
  404 Not Found
Err http://wine.budgetdedicated.com breezy/main Packages
  404 Not Found
Ign http://us.archive.ubuntu.com breezy Release.gpg
Ign http://us.archive.ubuntu.com breezy-updates Release.gpg
Ign http://us.archive.ubuntu.com breezy-backports Release.gpg
Ign http://us.archive.ubuntu.com breezy Release
Ign http://us.archive.ubuntu.com breezy-updates Release
Ign http://us.archive.ubuntu.com breezy-backports Release
Ign http://us.archive.ubuntu.com breezy/main Sources
Ign http://us.archive.ubuntu.com breezy/restricted Sources
Ign http://us.archive.ubuntu.com breezy/universe Packages
Ign http://us.archive.ubuntu.com breezy/main Packages
Ign http://us.archive.ubuntu.com breezy/restricted Packages
Ign http://us.archive.ubuntu.com breezy/universe Sources
Ign http://us.archive.ubuntu.com breezy-updates/main Packages
Ign http://us.archive.ubuntu.com breezy-updates/restricted Packages
Ign http://us.archive.ubuntu.com breezy-updates/main Sources
Ign http://us.archive.ubuntu.com breezy-updates/restricted Sources
Ign http://us.archive.ubuntu.com breezy-backports/main Packages
Ign http://us.archive.ubuntu.com breezy-backports/restricted Packages
Ign http://us.archive.ubuntu.com breezy-backports/universe Packages
Ign http://us.archive.ubuntu.com breezy-backports/multiverse Packages
Ign http://us.archive.ubuntu.com breezy-backports/main Sources
Ign http://us.archive.ubuntu.com breezy-backports/restricted Sources
Ign http://us.archive.ubuntu.com breezy-backports/universe Sources
Ign http://us.archive.ubuntu.com breezy-backports/multiverse Sources
Err http://us.archive.ubuntu.com breezy/main Sources
  404 Not Found
Err http://us.archive.ubuntu.com breezy/restricted Sources
  404 Not Found
Err http://us.archive.ubuntu.com breezy/universe Packages
  404 Not Found
Err http://us.archive.ubuntu.com breezy/main Packages
  404 Not Found
Err http://us.archive.ubuntu.com breezy/restricted Packages
  404 Not Found
Err http://us.archive.ubuntu.com breezy/universe Sources
  404 Not Found
Err http://us.archive.ubuntu.com breezy-updates/main Packages
  404 Not Found
Err http://us.archive.ubuntu.com breezy-updates/restricted Packages
  404 Not Found
Err http://us.archive.ubuntu.com breezy-updates/main Sources
  404 Not Found
Err http://us.archive.ubuntu.com breezy-updates/restricted Sources
  404 Not Found
Err http://us.archive.ubuntu.com breezy-backports/main Packages
  404 Not Found
Err http://us.archive.ubuntu.com breezy-backports/restricted Packages
  404 Not Found
Err http://us.archive.ubuntu.com breezy-backports/universe Packages
  404 Not Found
Err http://us.archive.ubuntu.com breezy-backports/multiverse Packages
  404 Not Found
Err http://us.archive.ubuntu.com breezy-backports/main Sources
  404 Not Found
Err http://us.archive.ubuntu.com breezy-backports/restricted Sources
  404 Not Found
Err http://us.archive.ubuntu.com breezy-backports/universe Sources
  404 Not Found
Err http://us.archive.ubuntu.com breezy-backports/multiverse Sources
  404 Not Found
Ign http://security.ubuntu.com breezy-security Release.gpg
Ign http://security.ubuntu.com breezy-security Release
Ign http://security.ubuntu.com breezy-security/main Packages
Ign http://security.ubuntu.com breezy-security/restricted Packages
Ign http://security.ubuntu.com breezy-security/main Sources
Ign http://security.ubuntu.com breezy-security/restricted Sources
Ign http://security.ubuntu.com breezy-security/universe Packages
Ign http://security.ubuntu.com breezy-security/universe Sources
Err http://security.ubuntu.com breezy-security/main Packages
  404 Not Found
Err http://security.ubuntu.com breezy-security/restricted Packages
  404 Not Found
Err http://security.ubuntu.com breezy-security/main Sources
  404 Not Found
Err http://security.ubuntu.com breezy-security/restricted Sources
  404 Not Found
Err http://security.ubuntu.com breezy-security/universe Packages
  404 Not Found
Err http://security.ubuntu.com breezy-security/universe Sources
  404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://wine.budgetdedicated.com/apt/dists/breezy/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by bluevoodoo1 on 2006-05-21
Maybe you could post your /etc/apt/sources.list   ??

---

### Post by aysiu on 2006-05-22
The US mirrors are buggy sometimes.

You might want to trade up your

[http://us.archive.ubuntu.com](http://us.archive.ubuntu.com)

for 

[http://archive.ubuntu.com](http://archive.ubuntu.com)

---

### Post by sparky25890 on 2006-05-22
```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe
deb http://wine.budgetdedicated.com/apt breezy main

```


theres my sources, and I also tried changing from us to normal, but still the same old 404 error.  Its wierd because if i copy the address and paste it into firefix, it works fine.

---

### Post by bluevoodoo1 on 2006-05-22
[QUOTE=sparky25890]


theres my sources, and I also tried changing from us to normal, but still the same old 404 error.  Its wierd because if i copy the address and paste it into firefix, it works fine.[/QUOTE]


After you changed your sources list, did you run...

```
sudo apt-get update
```

???

---

### Post by Al3xanR0 on 2006-05-22
Are you accessing the net via a proxy?

---

### Post by Al3xanR0 on 2006-05-22
Are you accessing the net via a proxy?

---

### Post by shrekkie on 2007-10-25
I have the same problem here, I'm using the net via a proxy and I'm positive I've configured it correctly in synaptic (settings->preferences->network).

I've tried many different sources and I still get the 404 error every time. This is absolutely killing me! Please help...

Here's my sources.list

```

# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://nz.archive.ubuntu.com/ubuntu edgy main restricted 
deb http://nz.archive.ubuntu.com/ubuntu edgy-updates main restricted
deb http://security.ubuntu.com/ubuntu edgy-security main restricted

deb-src http://nz.archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://nz.archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://nz.archive.ubuntu.com/ubuntu edgy universe multiverse 
deb http://nz.archive.ubuntu.com/ubuntu edgy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security universe multiverse

deb-src http://nz.archive.ubuntu.com/ubuntu edgy universe multiverse
deb-src http://nz.archive.ubuntu.com/ubuntu edgy-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security universe multiverse

# Seveas' Ubuntu Packages
# GPG key: 1135D466
deb http://mirror.ubuntulinux.nl/ edgy-seveas all 

deb-src http://mirror2.ubuntulinux.nl/ edgy-seveas all

# Ubuntu backports project
# GPG key: 437D05B5
deb http://nz.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse 

deb-src http://nz.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

# Canonical Commercial packages
# GPG key: 437D05B5
deb http://archive.canonical.com edgy-commercial main 

deb-src http://archive.canonical.com edgy-commercial main

```

---

