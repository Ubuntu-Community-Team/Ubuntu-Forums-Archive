---
title: "K3B broken &amp; alternative to devede?"
date: 2009-09-10
forum: General Help
---

### Post by sandyd on 2009-09-10
K3B package broken.
i never instealled K3B before... but heard some good things about it. so i decided to try.

unfortunately, it seems that theirs some things broken on my system..

anyone else having this?

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  k3b: Depends: kdelibs-data (>= 4:3.1.4-2)
E: Broken packages

```also, im currently using devede to create Video DVDs.

is there software that could create a DVD WITHOUT a menu, like commercial dvds? (sorry, i kinda find it anoying cause some of those movies are for my grandparents (and parents) and they have no idea how to use a remote control. other than the play, on/of, stop and pause buttons that is.

EDIT: heres my sources.list
```

#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to                       
# newer versions of the distribution.                                                           

deb http://ca.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.                                                
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any  
## review or updates from the Ubuntu security team.                        
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty universe                   
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty universe               
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates universe           
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates universe       

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in      
## multiverse WILL NOT receive any review or updates from the Ubuntu        
## security team.                                                           
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty multiverse                  
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty multiverse              
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse          
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse      

## Uncomment the following two lines to add software from the 'backports'
## repository.                                                           
## N.B. software from this repository may not have been tested as        
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.                               
 deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
 deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
 deb http://archive.canonical.com/ubuntu jaunty partner
 deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu intrepid main
deb http://download.virtualbox.org/virtualbox/debian jaunty non-free
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
deb http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"
deb http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu jaunty main ## Cairo-Dock-PPA
deb http://ppa.launchpad.net/awn-testing/ubuntu intrepid main
deb http://ppa.launchpad.net/neversfelde/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/neversfelde/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/kmess-packages/kmess-stable/ubuntu jaunty main
deb-src http://ppa.launchpad.net/kmess-packages/kmess-stable/ubuntu jaunty main

```

---

### Post by mikewhatever on 2009-09-10
You can try fixing broken packages with **sudo apt-get install -f**, however, the problem may also be in mixing repositories. You seem to have quite a bit of mixing there, kde3 and kde4, jaunty and Intrepid.

---

### Post by xx58 on 2009-09-14
:rolleyes:Karmic Koala 9.10 have k3b 1.66 alpha 2 package and stable version are k3b 1.05 and it need to install from source code and your problem are over. K3b 1.66 alpha 2 have too many problems.

---

### Post by stderr on 2009-09-14
> **carlee said:**
> im currently using devede to create Video DVDs.

is there software that could create a DVD WITHOUT a menu, like commercial dvds? (sorry, i kinda find it anoying cause some of those movies are for my grandparents (and parents) and they have no idea how to use a remote control. other than the play, on/of, stop and pause buttons that is.

Inside devede, you can click "Menu Options", and select "Jump to the first title at startup". This way, whilst you're still creating a menu, it will only (by default) be displayed when all the titles finish, as opposed to needing to navigate it to start playback. 

Furthermore, K3B simply uses wodim (if I remember correctly) to burn. You may as well just select "Advanced Options" in devede, and then "Create an ISO or BIN/CUE image". When you get the ISO, you can burn it simply using something like

```
cdrecord -v myfile.iso
```

---

