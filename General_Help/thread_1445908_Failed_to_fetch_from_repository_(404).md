---
title: "Failed to fetch from repository (404)"
date: 2010-04-03
forum: General Help
---

### Post by ali98ir on 2010-04-03
Update Manager fails to update the files in Karmic 9.10. The Internet access is fine but it fails to fetch from repository (404). I haven't changed any setting but since yesterday I realized the Update Manager is not working. I tried different servers and results were the same. It seems the packages are available in the server (checked by firefox), while Ubuntu can not find them. As I am using Bell-Sympatico as ISP, I am not behind any proxy.

Any idea?

Thanks,
Ali

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

##################################
##################################
##################################

cat /etc/apt/sources.list

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) karmic main restricted
deb-src [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) karmic main restricted #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) karmic-updates main restricted
deb-src [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) karmic-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

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
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) karmic-security main restricted
deb-src [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) karmic-security main restricted #Added by software-properties
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) hardy main
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) karmic free

##################################
##################################
##################################

Failed to fetch [http://deb.opera.com/opera/dists/stable/non-free/binary-i386/Packages.gz](http://deb.opera.com/opera/dists/stable/non-free/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/karmic/partner/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/karmic/partner/source/Sources.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/karmic/free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/karmic/free/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/hardy/main/source/Sources.gz](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/hardy/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://dl.google.com/linux/deb/dists/stable/main/binary-i386/Packages.gz](http://dl.google.com/linux/deb/dists/stable/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic/main/source/Sources.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic/restricted/source/Sources.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic/restricted/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-updates/main/source/Sources.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-updates/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-updates/restricted/source/Sources.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-updates/restricted/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-security/main/source/Sources.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-security/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-security/restricted/source/Sources.gz](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/karmic-security/restricted/source/Sources.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

###############

---

### Post by NCLI on 2010-04-03
Try selecting a different mirror from Software Sources. Going by the name of your mirror, it doesn't sound very official. As a general rule, try using the main repos, as the other ones can be down at times. The officially approved repos are under strict scrutiny, and are required to be very stable, and have a high uptime.

---

### Post by ali98ir on 2010-04-03
Hi NCLI

I tried many servers in Canada, US, UK, and the main server. All showing the same problem. Also, the option of "Select Best Server" in "Synaptic Package Manager" can not find any suitable mirror server.

Ali

---

### Post by ali98ir on 2010-04-06
My problem was fixed by removing "Google Chrome".

I realized that "Google Chrome", an Internet browser, introduces its proxy address to the Ubuntu's environmental variables. I needed to set the proxy address in the chrome to be able to access to my University Library. The Chrome makes a new variable containing that address, which blocks regular connections to the repositories. 

Firefox doesn't make that variable and therefore doesn't make any trouble for the update manager.

Ali

---

### Post by plurga on 2010-07-09
ok , so if u issue : 
 
apt-get update 
 
what u get ?? can u show me pls.

---

