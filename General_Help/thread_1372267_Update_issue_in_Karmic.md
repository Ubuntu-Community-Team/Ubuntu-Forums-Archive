---
title: "Update issue in Karmic"
date: 2010-01-04
forum: General Help
---

### Post by cmwatford on 2010-01-04
I haven't been able to do a complete update in months. Every time I use sudo apt-get update it spits out this. ```
Hit http://packages.medibuntu.org karmic Release.gpg
Ign http://packages.medibuntu.org karmic/free Translation-en_US                
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US            
Hit http://archive.canonical.com karmic Release.gpg                            
Ign http://archive.canonical.com karmic/partner Translation-en_US              
Ign http://archive.canonical.com karmic/deb-src Translation-en_US              
Hit http://packages.medibuntu.org karmic Release                               
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Ign http://archive.canonical.com karmic/http://archive.canonical.com/ubuntu Translation-en_US
Ign http://archive.canonical.com karmic/jaunty Translation-en_US               
Hit http://archive.canonical.com karmic Release                                
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US           
Hit http://packages.medibuntu.org karmic/free Packages               
Hit http://archive.ubuntu.com karmic Release.gpg                     
Ign http://archive.ubuntu.com karmic/main Translation-en_US                    
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://archive.canonical.com karmic/partner Packages                       
Hit http://packages.medibuntu.org karmic/non-free Packages                     
Get:1 http://packages.medibuntu.org karmic/free Sources [3,225B]     
Hit http://ppa.launchpad.net karmic Release                                
Ign http://archive.ubuntu.com karmic/restricted Translation-en_US              
Ign http://archive.ubuntu.com karmic/universe Translation-en_US            
Ign http://archive.ubuntu.com karmic/multiverse Translation-en_US          
Hit http://archive.ubuntu.com karmic-updates Release.gpg                   
Ign http://archive.ubuntu.com karmic-updates/main Translation-en_US        
Ign http://archive.ubuntu.com karmic-updates/restricted Translation-en_US  
Ign http://archive.ubuntu.com karmic-updates/universe Translation-en_US    
Ign http://archive.ubuntu.com karmic-updates/multiverse Translation-en_US  
Hit http://archive.ubuntu.com karmic-security Release.gpg                  
Hit http://ppa.launchpad.net karmic/main Packages                          
Hit http://ppa.launchpad.net karmic/main Sources                           
Get:2 http://packages.medibuntu.org karmic/non-free Sources [5,533B]       
Ign http://archive.ubuntu.com karmic-security/main Translation-en_US           
Hit http://ppa.launchpad.net karmic/main Packages
Ign http://archive.ubuntu.com karmic-security/restricted Translation-en_US
Ign http://archive.ubuntu.com karmic-security/universe Translation-en_US
Ign http://archive.ubuntu.com karmic-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com karmic Release
Hit http://archive.ubuntu.com karmic-updates Release
Hit http://archive.ubuntu.com karmic-security Release
Hit http://archive.ubuntu.com karmic/main Sources
Hit http://archive.ubuntu.com karmic/restricted Sources
Hit http://archive.ubuntu.com karmic/main Packages
Hit http://archive.ubuntu.com karmic/restricted Packages
Hit http://archive.ubuntu.com karmic/multiverse Sources
Hit http://archive.ubuntu.com karmic/universe Sources
Hit http://archive.ubuntu.com karmic/universe Packages
Hit http://archive.ubuntu.com karmic/multiverse Packages
Hit http://archive.ubuntu.com karmic-updates/main Packages
Hit http://archive.ubuntu.com karmic-updates/restricted Packages
Hit http://archive.ubuntu.com karmic-updates/restricted Sources
Hit http://archive.ubuntu.com karmic-updates/main Sources
Hit http://archive.ubuntu.com karmic-updates/multiverse Sources
Hit http://archive.ubuntu.com karmic-updates/universe Sources
Hit http://archive.ubuntu.com karmic-updates/universe Packages
Hit http://archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://archive.ubuntu.com karmic-security/main Packages
Hit http://archive.ubuntu.com karmic-security/restricted Packages
Hit http://archive.ubuntu.com karmic-security/restricted Sources
Hit http://archive.ubuntu.com karmic-security/main Sources
Hit http://archive.ubuntu.com karmic-security/multiverse Sources
Hit http://archive.ubuntu.com karmic-security/universe Sources
Hit http://archive.ubuntu.com karmic-security/universe Packages
Hit http://archive.ubuntu.com karmic-security/multiverse Packages
Fetched 8,758B in 1s (5,123B/s)
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/karmic/Release  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
``` My sources.list is this ```
# added by the release upgrader
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091027)]/ karmic main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic main restricted #Added by software-properties
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic main multiverse universe #Added by software-properties

##Ubuntu Tweak
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu karmic main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ karmic universe
deb http://archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ karmic-security universe
deb http://archive.ubuntu.com/ubuntu/ karmic-security multiverse
```I couldn't upgrade to karmic because of this as well. I ended up downloading the iso and installing from there. I've tried switching servers and that hasn't helped at all.
Any help would be greatly appreciated.:popcorn:

---

### Post by cariboo on 2010-01-04
Have you tried a different mirror? Go to System-->Administration-->Software Sources and click the Download from drop down and select Other, Click the Select Best Server button, and let it run it's course, once it is finished select the suggested server.

---

### Post by plucky on 2010-01-04
```
# added by the release upgrader
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091027)]/ karmic main restricted
#deb-src http://archive.ubuntu.com/ubuntu/ karmic main restricted #Added by software-properties
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ karmic main restricted
#deb-src http://archive.ubuntu.com/ubuntu/ karmic main multiverse universe #Added by software-properties

##Ubuntu Tweak
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu karmic main
#deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu karmic main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted
#deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ karmic universe
deb http://archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner [color=red]deb-src http://archive.canonical.com/ubuntu jaunty partner[/color]

deb http://archive.ubuntu.com/ubuntu/ karmic-security main restricted
#deb-src http://archive.ubuntu.com/ubuntu/ karmic-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ karmic-security universe
deb http://archive.ubuntu.com/ubuntu/ karmic-security multiverse
```


Try putting a # in front of all the lines that have "deb-src" and remove the line that I have highlighted in red.Then run "sudo apt-get update" again and see what occurs.

To edit the file ```
gksudo gedit /etc/apt/sources.list
```

Good Luck

---

### Post by t0p on 2010-01-04
Yeah that line highlighted by plucky is all wrong.  It should be *two* lines (one starting "deb", the next starting "deb-src") - plus the first half says "karmic" and the second half says "jaunty".  That's the malformed line mentioned in the error message.

---

