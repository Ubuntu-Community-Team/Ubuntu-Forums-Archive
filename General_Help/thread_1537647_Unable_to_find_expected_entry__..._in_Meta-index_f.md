---
title: "Unable to find expected entry  ... in Meta-index file (malformed Release file?)"
date: 2010-07-23
forum: General Help
---

### Post by kapokfly on 2010-07-23
Ubuntu 9.10, can someone let me know what is wrong? and what if I don't fix this issue?

> 
:~$ sudo apt-get update
Hit [http://ubuntu.cn99.com](http://ubuntu.cn99.com) karmic Release.gpg
Ign [http://ubuntu.cn99.com](http://ubuntu.cn99.com) karmic/non-free Translation-en_US                                                                                    
Ign [http://ubuntu.cn99.com](http://ubuntu.cn99.com) karmic/main Translation-en_US                                                                                        
Ign [http://ubuntu.cn99.com](http://ubuntu.cn99.com) karmic/universe Translation-en_US                                                                                    
Ign [http://ubuntu.cn99.com](http://ubuntu.cn99.com) karmic/restricted Translation-en_US                                                                                  
Ign [http://ubuntu.cn99.com](http://ubuntu.cn99.com) karmic/multiverse Translation-en_US                                                                                   
Get:1 [http://ubuntu.cn99.com](http://ubuntu.cn99.com) karmic-updates Release.gpg [189B]                                                                                   
Ign [http://ubuntu.cn99.com](http://ubuntu.cn99.com) karmic-updates/non-free Translation-en_US                                                                             
Ign [http://ubuntu.cn99.com](http://ubuntu.cn99.com) karmic-updates/main Translation-en_US                                                                                 
Ign [http://ubuntu.cn99.com](http://ubuntu.cn99.com) karmic-updates/universe Translation-en_US                                                                             
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                                                                                             
Ign [http://ubuntu.cn99.com](http://ubuntu.cn99.com) karmic-updates/restricted Translation-en_US                                                 
Ign [http://ubuntu.cn99.com](http://ubuntu.cn99.com) karmic-updates/multiverse Translation-en_US                                                 
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                                 
Hit [http://ubuntu.cn99.com](http://ubuntu.cn99.com) karmic Release                                                                              
Get:3 [http://ubuntu.cn99.com](http://ubuntu.cn99.com) karmic-updates Release [44.1kB]                                                           
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]                                                                                           
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable Release.gpg                                                                               
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable/main Translation-en_US                                              
Ign [http://oss.oracle.com](http://oss.oracle.com) unstable/non-free Translation-en_US                                          
Get:5 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,055B]                                               
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable Release                                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable/main Packages
Hit [http://oss.oracle.com](http://oss.oracle.com) unstable/non-free Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
Fetched 48.0kB in 2s (20.0kB/s)
W: Failed to fetch [http://ubuntu.cn99.com/ubuntu/dists/karmic/Release](http://ubuntu.cn99.com/ubuntu/dists/karmic/Release)  Unable to find expected entry  non-free/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://ubuntu.cn99.com/ubuntu/dists/karmic-updates/Release](http://ubuntu.cn99.com/ubuntu/dists/karmic-updates/Release)  Unable to find expected entry  non-free/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
Here is my source list:

> 
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) karmic non-free main universe restricted multiverse
deb-src [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) karmic non-free universe main multiverse restricted #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) karmic-updates non-free main universe restricted multiverse
deb-src [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) karmic-updates non-free main universe restricted multiverse #Added by software-properties

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
# deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner


deb [http://oss.oracle.com/debian](http://oss.oracle.com/debian) unstable main non-free
# deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) karmic non-free
# deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free



---

