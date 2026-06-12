---
title: "Update manager - malformed Release file"
date: 2010-08-23
forum: General Help
---

### Post by Fsmv on 2010-08-23
When I check for updates I get this error:
```

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-security/Release  Unable to find expected entry  multiverse\/source/Sources in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.
```Also it started 62 days ago, at the top it says the package information was last updated 62 days ago, so June 22nd. That's around the time I switched to a wired connection so I assume that's the problem. If I go to System > Preferences > Network Connections there is nothing under the wired tab. But I'm connected to the internet through an Ethernet connection. Even if I hit add and input the same settings from the interfaces file then name it eth0 it doesn't show up after I hit apply. Any ideas on how to fix it?

/etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0 
iface eth0 inet static
address 192.168.1.123
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
```

---

### Post by Fsmv on 2010-08-23
I found the file /etc/apt/sources.list it was
```

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb-src http://archive.ubuntu.com/ubuntu lucid-security multiverse\ multiverse #Added by software-properties
deb http://archive.ubuntu.com/ubuntu lucid-security multiverse\ main universe restricted

#Tor
deb http://archive.ubuntu.com/ubuntu lucid multiverse main universe restricted
deb-src http://archive.ubuntu.com/ubuntu lucid multiverse
deb http://archive.ubuntu.com/ubuntu lucid-updates universe main multiverse restricted
# deb http://deb.torproject.org/torproject.org karmic main

```I changed these lines
```

deb-src http://archive.ubuntu.com/ubuntu lucid-security multiverse multiverse #Added by software-properties
deb http://archive.ubuntu.com/ubuntu lucid-security multiverse main universe restricted

```

And now the error doesn't occur any more. I don't know how that backslash got in there though.

---

