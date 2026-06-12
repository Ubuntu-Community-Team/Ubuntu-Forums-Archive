---
title: "Ubuntu 10.04.4:sudo apt-get update error : (-5 - No address associated with hostname)"
date: 2012-05-09
forum: General Help
---

### Post by pawanmup on 2012-05-09
Hi I am having problem with the "sudo apt-get update", 

on,
> # lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:    10.04
Codename:    lucidBelow is my output

> sudo apt-get update
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) lucid Release.gpg
  Something wicked happened resolving 'jp.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Translation-en_US           
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US       
  Something wicked happened resolving 'jp.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                                                    
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US                                
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US  
  Something wicked happened resolving 'jp.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                      
Err [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US    
  Something wicked happened resolving 'jp.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US                                 
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                                                            
Err [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
.
.
.
W: Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-amd64/Packages.gz](http://jp.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-amd64/Packages.gz)  Something wicked happened resolving 'jp.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz](http://jp.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz)  Something wicked happened resolving 'jp.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-amd64/Packages.gz](http://jp.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-amd64/Packages.gz)  Something wicked happened resolving 'jp.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz](http://jp.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz)  Something wicked happened resolving 'jp.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.gz](http://jp.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.gz)  Something wicked happened resolving 'jp.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-amd64/Packages.gz](http://jp.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-amd64/Packages.gz)  Something wicked happened resolving 'jp.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz](http://jp.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz)  Something wicked happened resolving 'jp.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz](http://jp.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz)  Something wicked happened resolving 'jp.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-amd64/Packages.gz](http://jp.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-amd64/Packages.gz)  Something wicked happened resolving 'jp.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz](http://jp.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz)  Something wicked happened resolving 'jp.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-amd64/Packages.gz](http://jp.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-amd64/Packages.gz)  Something wicked happened resolving 'jp.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz](http://jp.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz)  Something wicked happened resolving 'jp.archive.ubuntu.com:http' (-5 - No address associated with hostname)
cat /etc/apt/sources.list

> # cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release amd64 (20120214.2)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
Please suggest me on how to resolve this issue , I am struggling with many attempts googling and no luck

---

### Post by 2F4U on 2012-05-09
Do you still have the problem? It may be a temporary outage of the repository server. If the problem still exists, try to select a different repository server in Update Manager.

---

### Post by pawanmup on 2012-05-10
I am still facing issue , can anybody suggest.

---

