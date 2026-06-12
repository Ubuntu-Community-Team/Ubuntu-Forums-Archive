---
title: "404 on certain updates..?"
date: 2009-08-24
forum: General Help
---

### Post by BigB'sLinux on 2009-08-24
Used Snaptic and got this: >  Failed to fetch [http://ppa.launchpad.net/adnarim/ubuntu/dists/jaunty/main/binary-i386/Packages](http://ppa.launchpad.net/adnarim/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found Failed to fetch [http://ppa.launchpad.net/adnarim/ubuntu/dists/jaunty/main/source/Sources](http://ppa.launchpad.net/adnarim/ubuntu/dists/jaunty/main/source/Sources)  404 Not Found Some index files failed to download, they have been ignored, or old ones used instead.   I tried sudo, reloaded my sources list, nothing will help. I have Tor installed, but I dont know If I have to change my sources list or something?   >  # deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to # newer versions of the distribution.  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty restricted main multiverse universe #Added by software-properties  ## Major bug fix updates produced after the final release of the ## distribution. deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates restricted main multiverse universe #Added by software-properties  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu ## team. Also, please note that software in universe WILL NOT receive any ## review or updates from the Ubuntu security team. deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  ## team, and may not be under a free licence. Please satisfy yourself as to  ## your rights to use the software. Also, please note that software in  ## multiverse WILL NOT receive any review or updates from the Ubuntu ## security team. deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse  ## Uncomment the following two lines to add software from the 'backports' ## repository. ## N.B. software from this repository may not have been tested as ## extensively as that contained in the main release, although it includes ## newer versions of some applications which may provide useful features. ## Also, please note that software in backports WILL NOT receive any review ## or updates from the Ubuntu security team. # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse  ## Uncomment the following two lines to add software from Canonical's ## 'partner' repository. ## This software is not part of Ubuntu, but is offered by Canonical and the ## respective vendors as a service to Ubuntu users. deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security main restricted deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security restricted main multiverse universe #Added by software-properties deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security universe deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security multiverse deb [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) jaunty main deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) jaunty main deb [http://ppa.launchpad.net/adnarim/ubuntu](http://ppa.launchpad.net/adnarim/ubuntu) jaunty main deb-src [http://ppa.launchpad.net/adnarim/ubuntu](http://ppa.launchpad.net/adnarim/ubuntu) jaunty main   Any help would really be appreciated.   Sudo aptitude update returned these errors:   >  Err [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              404 Not Found   >   and this:  [quote] Err [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources         404 Not Found     Everything else updates fine. Are they unsupported packages?

---

### Post by BigB'sLinux on 2009-08-24
anybody home?

---

### Post by BigB'sLinux on 2009-08-28
I hate to bump my own thread, but three days,no response? Can anyone in Ubuntu land explain to me what to do to remedy this issue?   Or If you need more input just ask. I need to fix this problem..   do I just delete the 404 sources on my sources.list? Change them to another repo? I have 3rd party software, but this is my main sources and main packages..?  :   >  Failed to fetch [http://ppa.launchpad.net/adnarim/ubuntu/dists/jaunty/main/binary-i386/Packages](http://ppa.launchpad.net/adnarim/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found [quote] Failed to fetch [http://ppa.launchpad.net/adnarim/ubuntu/dists/jaunty/main/source/Sources](http://ppa.launchpad.net/adnarim/ubuntu/dists/jaunty/main/source/Sources)  404 Not Found [/qoute] 
[quote] Some index files failed to download, they have been ignored, or old ones used instead. [/qoute]   These 404's are driving me crazy and I cant find 'any' info on the exact issue Im having and I dont want to get h4x3d over out of date software.   Thanks in advance...BBL  edit- someone on IRC said I can just delete the launchpad source of the 404 entry in my sources.list. Can someone please confirm this? Some help would be appreciated I have been researching this day and night and its starting to get in the way of my business-thanx

---

### Post by LADmaticCA on 2009-08-28
I found this thread that appears to have a similar issue:  [http://ubuntuforums.org/archive/index.php/t-938470.html](http://ubuntuforums.org/archive/index.php/t-938470.html)
Their solution was in the synaptic preferences, network setup. 

I'm still fairly new to Ubuntu but I wanted suggest maybe changing your download source in System > Administration > Software Sources. Where it ask you where to download from select "Other" and do a scan for the best network.

---

### Post by BigB'sLinux on 2009-08-28
thnks Ill check it out

---

### Post by BigB'sLinux on 2009-08-28
thanks, but I believe the repos Im talking about are either not in service or never were meant to be. I did download things like Tor and other rd party software where updates may not be supported.   I really think I may need to delete the bunk links from my sources.list, but then again I dont want to make any mistakes and mess up my system. I dont have a sh**load of 404's just the above mentioned 2.   I would just delete them, but /main Sources and /main Packages intimidates me..Help!  

  [SOLVED] (I guess..?) I Just commented them out. If someone has a better option dont be shy

---

