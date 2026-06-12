---
title: "Could not download all repository indexes"
date: 2010-02-28
forum: General Help
---

### Post by sbelz79 on 2010-02-28
When I open Update Manager and click "check," it starts downloading package information and then the following pops up:

> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://archive.ubuntu.com/dists/karmic/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/dists/karmic/main/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/dists/karmic/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/dists/karmic/universe/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.88.45 80]
Some index files failed to download, they have been ignored, or old ones used instead.

I opened Software Sources to try and remove the repositories, but couldn't find them.  Plus I'm not sure if I need to manually replace these repositories with newer ones- I'm still relatively new at using Ubuntu (made the full switch from windows in October 2009).

Plus, whenever I do install updates with the update manager, the "last updated" time doesn't reset itself.  It finishes installing the selected packages, and the message at the top of the Update Manager window reads "Your system is up-to-date.  The package information was last updated 28 days ago.

Using Ubuntu 9.10 x86_64

---

### Post by warp99 on 2010-02-28
Don't remove the repositories from your list since it may only be a temporary issue with the server, which it appears to be so. Just open a terminal and issue the following command:

```
sudo apt-get update
```

Post any errors that you may see.

---

### Post by sbelz79 on 2010-02-28
> **warp99 said:**
> Don't remove the repositories from your list since it may only be a temporary issue with the server, which it appears to be so. Just open a terminal and issue the following command:

```
sudo apt-get update
```

Post any errors that you may see.

I did so; here's some of the output (just the part at the end where the errors are):


> 
---------------------------------
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
  404  Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages
  404  Not Found [IP: 91.189.88.45 80]
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                                                                                                                        
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [909B]
Fetched 3,638B in 2min 0s (30B/s)                                                                                                                                                                             
W: Failed to fetch [http://archive.ubuntu.com/dists/karmic/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/dists/karmic/main/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch [http://archive.ubuntu.com/dists/karmic/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/dists/karmic/universe/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.88.45 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
me@computer:~$ 

---

### Post by warp99 on 2010-02-28
Please post or attach your '/etc/apt/sources.list' file. It appears there may be an error in one or two of the entries. We can fix that pretty easy.

---

### Post by sbelz79 on 2010-03-02
/etc/apt/sources.list:

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) karmic main
deb [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic main universe



deb [http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu) karmic cairo-dock ## Cairo-Dock-Stable

---

### Post by warp99 on 2010-03-03
Remove this line:

```
deb http://archive.ubuntu.com karmic main universe
```

and everything should be good to go.

---

### Post by sbelz79 on 2010-03-03
Don't I need that?

---

### Post by warp99 on 2010-03-03
> **sbelz79 said:**
> Don't I need that?

No, it's the wrong string and you already have those repositories listed.

```
deb http://us.archive.ubuntu.com/ubuntu/ karmic **main** restricted
deb http://us.archive.ubuntu.com/ubuntu/ karmic **universe**
```

---

### Post by sbelz79 on 2010-03-03
OK cool, I'm able to update without getting errors now.  Thanks!

---

