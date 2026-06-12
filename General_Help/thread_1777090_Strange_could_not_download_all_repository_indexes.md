---
title: "Strange: could not download all repository indexes"
date: 2011-06-07
forum: General Help
---

### Post by onako on 2011-06-07
Recently I noticed a red warning sign that suggest there are some problems with update information.
After clicking on it, and reloading, I obtain:
Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-amd64/Packages.gz](http://de.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-amd64/Packages.gz)  404  Not Found [IP: 141.30.13.30 80]
Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-amd64/Packages.gz](http://de.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-amd64/Packages.gz)  404  Not Found [IP: 141.30.13.30 80]
Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-amd64/Packages.gz](http://de.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-amd64/Packages.gz)  404  Not Found [IP: 141.30.13.30 80]
Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-amd64/Packages.gz](http://de.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-amd64/Packages.gz)  404  Not Found [IP: 141.30.13.30 80]
Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/source/Sources.gz](http://de.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/source/Sources.gz)  404  Not Found [IP: 141.30.13.30 80]
Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/source/Sources.gz](http://de.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/source/Sources.gz)  404  Not Found [IP: 141.30.13.30 80]
Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/source/Sources.gz](http://de.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/source/Sources.gz)  404  Not Found [IP: 141.30.13.30 80]
Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/source/Sources.gz](http://de.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/source/Sources.gz)  404  Not Found [IP: 141.30.13.30 80]
Some index files failed to download, they have been ignored, or old ones used instead.

....................
typing "sudo apt-get dist-upg.rade" outputs:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded:
........................
What might be the problem?
Thanks

---

### Post by coffeecat on 2011-06-07
When I click on your first URL, this reveals itself as  the problem:

> 
**Not Found**

 The requested URL /ubuntu/dists/[COLOR=Red]jaunty[/COLOR]-backports/main/binary-amd64/Packages.gz was not found on this server.
Jaunty is unsupported and has been for about 8 months now. When was the last time you tried an update? :)

If you are running Jaunty you need to upgrade either by re-installing with a supported version or by upgrading in situ. The latter will be uncertain because you would need to use the old-releases repository and upgrade via Karmic which is also now unsupported. A fresh install would be preferable, in my opinion.

That, of course, is if you are running Jaunty. If you are running Lucid or later and somehow there are some residual Jaunty lines in your sources.list, then that needs editing. Which version of Ubuntu are you running?

---

### Post by onako on 2011-06-07
This is the info I get:
You are using Ubuntu 10.04 LTS
 - the Lucid Lynx - released in April 2010 and supported until April 2013.
......................
Note that I'm regularly updating the system, and the problem
occurred only recently.

---

### Post by philinux on 2011-06-07
> **onako said:**
> This is the info I get:
You are using Ubuntu 10.04 LTS
 - the Lucid Lynx - released in April 2010 and supported until April 2013.
......................
Note that I'm regularly updating the system, and the problem
occurred only recently.

Post back the output of this.

```
cat /etc/apt/sources.list
```

---

### Post by onako on 2011-06-07
Here is the output:

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse

# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free # disabled on upgrade to lucid
.............................................
I hope this is not some big problem.

---

### Post by philinux on 2011-06-07
```
gksu gedit /etc/apt/sources.list
```

Look at this section.
```
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ **jaunty**-backports main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ **jaunty**-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu **jaunty** partner
# deb-src http://archive.canonical.com/ubuntu **jaunty** partner
```

Change jaunty to lucid and then save the file.

---

### Post by onako on 2011-06-07
Thanks! It worked.

---

