---
title: "php5-dev package / phpize"
date: 2011-11-26
forum: General Help
---

### Post by sanukcm on 2011-11-26
Hi all. 

Running 64bit version of 11.10 on a new machine and trying to set up xdebug for PHP.


```
$:~pecl install xdebug
```
yields: 

```

WARNING: channel "pecl.php.net" has updated its protocols, use "pecl channel-update pecl.php.net" to update
downloading xdebug-2.1.2.tgz ...
Starting to download xdebug-2.1.2.tgz (304,229 bytes)
..............................................................done: 304,229 bytes
66 source files, building
running: phpize
sh: phpize: not found
ERROR: `phpize' failed
```

I found several folks [[1]("http://www.semanticpool.de/phpize-not-found/")][[2]("http://h3x.no/2010/07/09/sh-phpize-not-found")][[3]("http://en.kioskea.net/faq/637-phpize-command-not-found")] that report that phpize is part of the php5-dev package. 

Unfortunately, 

```
sudo apt-get install php5-dev
```

yields: 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package php5-dev
```

here is my sources.list file: 

```
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu oneiric main restricted
deb-src http://archive.ubuntu.com/ubuntu oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu oneiric-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu oneiric universe
deb-src http://archive.ubuntu.com/ubuntu oneiric universe
deb http://archive.ubuntu.com/ubuntu oneiric-updates universe
deb-src http://archive.ubuntu.com/ubuntu oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu oneiric multiverse
deb-src http://archive.ubuntu.com/ubuntu oneiric multiverse
deb http://archive.ubuntu.com/ubuntu oneiric-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu oneiric-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu oneiric-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://archive.ubuntu.com/ubuntu oneiric-security main restricted
deb http://archive.ubuntu.com/ubuntu oneiric-security universe
deb-src http://archive.ubuntu.com/ubuntu oneiric-security universe
deb http://archive.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://archive.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
deb http://archive.canonical.com/ lucid partner
deb-src http://archive.canonical.com/ lucid partner
deb http://archive.canonical.com/ubuntu oneiric oneric partner
deb-src http://archive.canonical.com/ubuntu oneiric oneric partner

deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart 11.10 10gen
```

Any ideas? 

Thanks!

---

