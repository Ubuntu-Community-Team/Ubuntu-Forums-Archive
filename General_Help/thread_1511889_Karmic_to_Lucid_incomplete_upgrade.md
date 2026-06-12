---
title: "Karmic to Lucid incomplete upgrade"
date: 2010-06-17
forum: General Help
---

### Post by kadal27 on 2010-06-17
(Though there are several threads regarding "Could not download all repository indexes", none of them helped me and hence I am starting this thread.)
I have upgraded from 9.10 to 10.04 using alternative CD.  The upgrade was not successful.  After several tries, I have got it upgraded.
But still I am getting "Could not download all repository indexes" error.  And also, I am unable to install mplayer and mencoder.
Error messages:
for sudo apt-get update
> Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1) lucid Release.gpg
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)/ lucid/main Translation-en_IN
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)/ lucid/restricted Translation-en_IN
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1) lucid Release
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1) lucid/main Packages
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1) lucid/restricted Packages
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1) lucid/main Packages
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1) lucid/restricted Packages
Err cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1) lucid/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1) lucid/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates Release.gpg                    
Ign [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/) all/main Translation-en_IN
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                                
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IN             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security/main Translation-en_IN  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) lucid/main Translation-en_IN   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_IN         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release                                    
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security/universe Translation-en_IN
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security/multiverse Translation-en_IN
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) karmic/main Translation-en_IN
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources             
Get:1 [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all Release.gpg [197B]                 
Get:2 [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all Release [961B]                      
Ign [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all Release                               
Ign [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main Packages                         
Ign [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main Packages                         
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-updates/main Translation-en_IN 
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-updates/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-updates/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates Release                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Packages                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Packages            
Hit [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main Packages                         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Sources                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Sources             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Packages              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Sources               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Packages            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Sources             
Fetched 198B in 12s (16B/s)                                                    
W: GPG error: [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CCC158AFC1289A29
W: Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.for cat /etc/apt/sources.list
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

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

deb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main
deb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/ lucid main restricted
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/ lucid main restricted
deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/ lucid main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main universefor sudo apt-get install mplayer
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: mplayer-skin but it is not installable
           Depends: mplayer-nogui but it is not going to be installed
           Depends: libfaac0 (>= 1.26) but it is not installable
E: Broken packagesThough I am using ubuntu for more than a year, I am not technically sound.
Please, offer me a detailed help.

---

### Post by arrange on 2010-06-17
Can you post the output from the [Terminal](https://help.ubuntu.com/community/GnomeTerminal)?```
uname -a
```
Why did you upgrade using the CD?

---

### Post by kadal27 on 2010-06-17
Output for uname -a
> Linux arivukkadal 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

---

### Post by wilee-nilee on 2010-06-17
Take the cd out if it's still in and change the repository from software sources using the other function and select best server to start with. Also the cat apt list is full of karmic when it should be Lucid if that is where your at.

---

### Post by wilee-nilee on 2010-06-17
To be honest with the apt-list reading all. Karmic it is really hard to see whats happened, and the update trying to read the cd when it is # ticked off in the apt list. I would backup your setup and do a fresh install if is were me.

---

### Post by arrange on 2010-06-18
Yes, back up your */home* and do a clean install 
or
change your */etc/apt/sources.list* into
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://in.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

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

# deb http://downloads.sourceforge.net/pro...la/mozilla/apt all main
# deb http://downloads.sourceforge.net/pro...la/mozilla/apt all main

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/ lucid main restricted
deb http://archive.ubuntu.com/ubuntu lucid main universe 

```and then run```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```But the result is uncertain :p

---

### Post by kadal27 on 2010-06-18
Is there no other option, that clean install?
How to restore /home after clean install and what will be the things restored that way?

---

### Post by arluijen on 2010-07-23
the solution arrange suggested worked fine by me...

---

