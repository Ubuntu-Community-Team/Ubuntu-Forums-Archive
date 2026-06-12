---
title: "Updating problem. Bad sources list? Pls check!"
date: 2011-04-09
forum: General Help
---

### Post by listerdl on 2011-04-09
Hi if I run:

```
sudo apt-get update
```

I get an error like this:

```
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
```

With more precise info:

```
Failed to fetch [COLOR="Red"]http://ppa.launchpad.net/ubuntu-mozilla-dail/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found[/COLOR]
Some index files failed to download, they have been ignored, or old ones used instead. 
``` 

Now the weird thing is that the above URL in red is not in the sources list file.

Any idea what I need to do here?

Thanks.

Appreciate all help!

This is my sources.list

```
 # deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://jp.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://jp.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://jp.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://jp.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://jp.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://jp.archive.ubuntu.com/ubuntu/ lucid universe
deb http://jp.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://jp.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://jp.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://jp.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://jp.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://jp.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://jp.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://jp.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://archive.canonical.com/ lucid partner
deb http://ppa.launchpad.net/klaus-vormweg/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/klaus-vormweg/ppa/ubuntu lucid main
```

---

### Post by ~Plue on 2011-04-09
> 
~snip
[http://ppa.launchpad.net](http://ppa.launchpad.net)/[COLOR=Red]ubuntu-mozilla-dail[/COLOR]/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gztheres a small typo when you added that PPA. it should read ubuntu-mozilla-dail[COLOR=Red]y[/COLOR]

you could change it from synaptic > edit menu > repositories > third party repositories (something like that, cant recall the exact wording)
> 
Now the weird thing is that the above URL in red is not in the sources list file.PPAs added though synaptic or add-apt-repository would be kept in seperate files in the directory /etc/apt/sources.list.d/

---

### Post by kiyop on 2011-04-09
The line may be in a file in directory /etc/apt/sources.list.d/
```
grep -n[COLOR=Black] ubuntu-mozilla [/COLOR]/etc/apt/sources.list.d/*
```

---

### Post by listerdl on 2011-04-09
thanks for that 

I saw that typo but i thought it might have been intentional - in any event i removed it (there was an identical but well typed URL) and there are no probs

Thanks again!

---

