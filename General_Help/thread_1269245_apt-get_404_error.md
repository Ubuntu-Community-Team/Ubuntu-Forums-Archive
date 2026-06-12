---
title: "apt-get 404 error"
date: 2009-09-18
forum: General Help
---

### Post by GiantEgg on 2009-09-18
Hi, nice to be here :)

I was hesitant to start another thread about a problem that seems to be fairly common, but I've combed Google and these forums for a few days and not come up with a good fix. - I'm pretty new but I'll try to include as much info in my first post as possible.

I'm running ubuntu 9.04 in a VM with a mac os x host, on a bridged connection. (ubuntu has a static IP)

I'm trying to install a few things I need to get some software up and running.

typing
```

apt-get install openssl
```was giving me me a 404 similar to the error i'm about to explain, but in my test before posting this it decided to work, and tells me I already have the latest version, so I'll worry about that again when the problem arises.


However I'm still having issues running:
```
apt-get update
```it results in:
```

Ign http://us.archive.ubuntu.com jaunty Release.gpg
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates Release.gpg
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com jaunty Release
Ign http://us.archive.ubuntu.com jaunty-updates Release
Ign http://security.ubuntu.com jaunty-security Release.gpg
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com jaunty-security Release
Ign http://security.ubuntu.com jaunty-security/main Packages
Ign http://security.ubuntu.com jaunty-security/restricted Packages
Ign http://security.ubuntu.com jaunty-security/main Sources
Ign http://security.ubuntu.com jaunty-security/restricted Sources
Ign http://security.ubuntu.com jaunty-security/universe Packages
Ign http://security.ubuntu.com jaunty-security/universe Sources
Ign http://security.ubuntu.com jaunty-security/multiverse Packages
Ign http://security.ubuntu.com jaunty-security/multiverse Sources
Ign http://us.archive.ubuntu.com jaunty/main Packages
Ign http://us.archive.ubuntu.com jaunty/restricted Packages
Ign http://us.archive.ubuntu.com jaunty/main Sources
Ign http://us.archive.ubuntu.com jaunty/restricted Sources
Ign http://us.archive.ubuntu.com jaunty/universe Packages
Ign http://us.archive.ubuntu.com jaunty/universe Sources
Ign http://us.archive.ubuntu.com jaunty/multiverse Packages
Ign http://us.archive.ubuntu.com jaunty/multiverse Sources
Ign http://us.archive.ubuntu.com jaunty-updates/main Packages
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Packages
Ign http://us.archive.ubuntu.com jaunty-updates/main Sources
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Sources
Ign http://us.archive.ubuntu.com jaunty-updates/universe Packages
Ign http://us.archive.ubuntu.com jaunty-updates/universe Sources
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
Ign http://us.archive.ubuntu.com jaunty/main Packages
Ign http://us.archive.ubuntu.com jaunty/restricted Packages
Ign http://us.archive.ubuntu.com jaunty/main Sources
Ign http://security.ubuntu.com jaunty-security/main Packages
Ign http://security.ubuntu.com jaunty-security/restricted Packages
Ign http://security.ubuntu.com jaunty-security/main Sources
Ign http://security.ubuntu.com jaunty-security/restricted Sources
Ign http://security.ubuntu.com jaunty-security/universe Packages
Ign http://security.ubuntu.com jaunty-security/universe Sources
Ign http://security.ubuntu.com jaunty-security/multiverse Packages
Ign http://us.archive.ubuntu.com jaunty/restricted Sources
Ign http://us.archive.ubuntu.com jaunty/universe Packages
Ign http://us.archive.ubuntu.com jaunty/universe Sources
Ign http://us.archive.ubuntu.com jaunty/multiverse Packages
Ign http://us.archive.ubuntu.com jaunty/multiverse Sources
Ign http://us.archive.ubuntu.com jaunty-updates/main Packages
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Packages
Ign http://us.archive.ubuntu.com jaunty-updates/main Sources
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Sources
Ign http://us.archive.ubuntu.com jaunty-updates/universe Packages
Ign http://us.archive.ubuntu.com jaunty-updates/universe Sources
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
Ign http://security.ubuntu.com jaunty-security/multiverse Sources
Err http://security.ubuntu.com jaunty-security/main Packages
  404 Not Found
Err http://security.ubuntu.com jaunty-security/restricted Packages
  404 Not Found
Err http://security.ubuntu.com jaunty-security/main Sources
  404 Not Found
Err http://security.ubuntu.com jaunty-security/restricted Sources
  404 Not Found
Err http://security.ubuntu.com jaunty-security/universe Packages
  404 Not Found
Err http://security.ubuntu.com jaunty-security/universe Sources
  404 Not Found
Err http://security.ubuntu.com jaunty-security/multiverse Packages
  404 Not Found
Err http://security.ubuntu.com jaunty-security/multiverse Sources
  404 Not Found
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
Err http://us.archive.ubuntu.com jaunty/main Packages
  404 Not Found
Err http://us.archive.ubuntu.com jaunty/restricted Packages
  404 Not Found
Err http://us.archive.ubuntu.com jaunty/main Sources
  404 Not Found
Err http://us.archive.ubuntu.com jaunty/restricted Sources
  404 Not Found
Err http://us.archive.ubuntu.com jaunty/universe Packages
  404 Not Found
Err http://us.archive.ubuntu.com jaunty/universe Sources
  404 Not Found
Err http://us.archive.ubuntu.com jaunty/multiverse Packages
  404 Not Found
Err http://us.archive.ubuntu.com jaunty/multiverse Sources
  404 Not Found
Err http://us.archive.ubuntu.com jaunty-updates/main Packages
  404 Not Found
Err http://us.archive.ubuntu.com jaunty-updates/restricted Packages
  404 Not Found
Err http://us.archive.ubuntu.com jaunty-updates/main Sources
  404 Not Found
Err http://us.archive.ubuntu.com jaunty-updates/restricted Sources
  404 Not Found
Err http://us.archive.ubuntu.com jaunty-updates/universe Packages
  404 Not Found
Err http://us.archive.ubuntu.com jaunty-updates/universe Sources
  404 Not Found
Err http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
  404 Not Found
Err http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
  404 Not Found
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources  404 Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources  404 Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources  404 Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources  404 Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources  404 Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources  404 Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources  404 Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```as I said I've been looking for days and I'm pretty much at my whits end.
I've rebuilt my sources.list from [http://repogen.simplylinux.ch/generate.php](http://repogen.simplylinux.ch/generate.php) and had the same problem. (sources.list shown above is the original)

I'm operating from behind a proxy, but after running:
```
export http_proxy=http://someuser:somepass@proxyserver
``` apt-get hasn't had a problem until now.



Here is the contents of my sources.list:
```

#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse

```The only change I've made recently (and I can't remember whether of not I've used apt-get since then) is to set a static IP, and bridge that connection with the Imac.
I intend to reverse that soon to see if it could be the problem, but since I'm posting this from ubuntu I doubt it. (can't change it now because it's running our nagios server!)

Sorry if some of this is out of order, kind of thinking of things as I go, and that's about all I can think of!
Cheers for any advice or suggestions

weekend... I need a beer :(

---

### Post by MelDJ on 2009-09-18
try changing your software server

---

### Post by GiantEgg on 2009-09-20
Okay, changed my software server in synaptic, that updated happily with new sources and everything, still get ```
W: Failed to fetch http://mirror.3fl.net.au/ubuntu/dists/jaunty-security/multiverse/source/Sources  404 Not Found

```
Also tried removing the static IP and bridged connection to the mac - problem persisted :(


Might add that I can still use synaptic.. so i'm not in dire straights, but apt-get would still be nice.

---

