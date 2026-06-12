---
title: "Repositories Problem!!!!!!!"
date: 2011-04-02
forum: General Help
---

### Post by fadi hamadneh on 2011-04-02
i am using ubuntu 10.04 LTS ..
everythiing was ok 
but after i installed selinux ... many problems happened ... i tries to fix them by google and ubuntu forums thread ... like i uninstalled selinux and installed apparmor .. 
problems related to PUBKEY happened when trying sudo apt-get update 

at last i want to show you the output of : apt-get update & cat /etc/apt/sources.list commands:

**sudo apt-get update:**

[COLOR=Red]fadi-admin@fadi-admin-laptop:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net/bean123ch/burg/ubuntu/](http://ppa.launchpad.net/bean123ch/burg/ubuntu/) karmic/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://ppa.launchpad.net/s-lagui/ppa/ubuntu/](http://ppa.launchpad.net/s-lagui/ppa/ubuntu/) lucid/main Translation-en_US  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/songbird-daily/ppa/ubuntu/](http://ppa.launchpad.net/songbird-daily/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages                       
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages               
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid Release.gpg             
Ign [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid Release
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates Release
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid/main Packages
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid/restricted Packages
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid/main Sources
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid/restricted Sources
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid/universe Packages
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid/universe Sources
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates/multiverse Sources
Reading package lists... Done

[/COLOR]**cat /etc/apt/sources.list**


[COLOR=Red]fadi-admin@fadi-admin-laptop:~$ cat /etc/apt/sources.list 
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) lucid universe
# deb [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main
# deb-src [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main
deb [http://ppa.launchpad.net/bean123ch/burg/ubuntu](http://ppa.launchpad.net/bean123ch/burg/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/bean123ch/burg/ubuntu](http://ppa.launchpad.net/bean123ch/burg/ubuntu) karmic main
# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb apps[/COLOR]

Please help me ins this issue waiting your replies guys

---

### Post by davidmohammed on 2011-04-02
you've got a few ppa items that are still linked to karmic - this is a bad idea and could cause update issues.  Go to your software sources and untick the ppa's with karmic - OR edit those software sources and change karmic to lucid.

as to the pubkey issues - please post in a reply the pubkey errors.  They should be easy enough to fix.

---

### Post by CharlesA on 2011-04-02
Duplicate thread can be found here:
[http://ubuntuforums.org/showthread.php?t=1719449](http://ubuntuforums.org/showthread.php?t=1719449)

---

