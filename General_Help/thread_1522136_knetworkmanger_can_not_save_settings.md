---
title: "knetworkmanger can not save settings"
date: 2010-07-01
forum: General Help
---

### Post by ulao on 2010-07-01
I have seen this issue in a few places 

[http://ubuntuforums.org/showthread.php?t=935841](http://ubuntuforums.org/showthread.php?t=935841)  for example. but the fix no longer works? 

I added 
```
deb http://ppa.launchpad.net/network-manager/trunk/ubuntu karmic main
deb-src http://ppa.launchpad.net/network-manager/trunk/ubuntu karmic main
```

and get 
```
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 248DD1EEBC8EBFE8
```

also get these but I think its unrelated
```


W: Failed to fetch http://people.debian.org/~dexter/dists/php5/woody/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://people.debian.org/~dexter/dists/php5/woody/source/Sources.gz  404 Not Found


```

--- Update ok I was able to use 
sudo apt-key adv --keyserver keys.nayr.net  --recv-keys 248DD1EEBC8EBFE8
to do it. but there are no updates for knetworkmanager.

```

 sudo apt-get install knetworkmanager
Reading package lists... Done
Building dependency tree
Reading state information... Done
knetworkmanager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 274 not upgraded.

```


---ok made it worse... I figure why not removal and re-install

I removed knetworkmanager, and reisntall says its now called network-manager-kde
 so I tried to install that but its already installed? So I removed that one. Not, I can not install either 
> 
Package network-manager-kde is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
 - confused?

Also thinking my lists are in bad shape. What should I have in there for 7.10
```


deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


# sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080701)]/ hardy main restricted

#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080701)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ Gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ Gutsy main restricted

## for network manger
deb http://ppa.launchpad.net/network-manager/trunk/ubuntu Gutsy main
deb-src http://ppa.launchpad.net/network-manager/trunk/ubuntu Gutsy main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb http://www.backports.org/debian  stable ucf
deb http://people.debian.org/~dexter php5 woody
deb-src http://people.debian.org/~dexter php5 woody


```

---

