---
title: "sources.list"
date: 2010-05-03
forum: General Help
---

### Post by Sin@Sin-Sacrifice on 2010-05-03
So ummm... I get "Ign [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) lucid/main" after apt-get update. I went to the site and everything is there. I'm at a loss.

---

### Post by dino99 on 2010-05-03
where is the problem ?

[http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/lucid/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/lucid/)

Location: A hole in the ground  

how do get connected ?

---

### Post by Sin@Sin-Sacrifice on 2010-05-03
I would say the problem is the "Ign" part of what I posted...

---

### Post by WorMzy on 2010-05-03
Backup your file
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```then run
```
sudo gedit /etc/apt/sources.list
```and paste the following into it (replacing what's already there):
```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

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
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
```That's a copy of my sources.list, and it works.

---

### Post by Sin@Sin-Sacrifice on 2010-05-03
No... the only problem is the XBMC repo... everything else works. For some reason it ignores the one in the OP. Thanks anyway.

---

### Post by WorMzy on 2010-05-03
Oh, I see. Well, try removing that line and adding: ```
[FONT=monospace]deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu lucid main[/FONT]
```
in it's place

---

### Post by Sin@Sin-Sacrifice on 2010-05-03
To make this easier here's my sources.list: ```
# 
# deb cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)]/ lucid main restricted

# deb cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

##XBMC and such...
deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu lucid main
```

As you can see that's what I have. apt-get update gives me no errors but apt-cache search xbmc gives me nothing. I don't get why it's ignoring them. I tried the ppa:xbmc crap from the site but it says the key isn't in the server so I got rid of that and added the repos and key manually. Now apt ignores the repo entirely.

Thanks again for the help.

---

### Post by Sin@Sin-Sacrifice on 2010-05-03
Don't know if it's relevant but others are being ignored too. Just noticed
```
Killmandline:$ sudo apt-get update
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US       
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/ lucid/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release                          
Hit http://us.archive.ubuntu.com lucid Release.gpg                             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US          
Hit http://archive.canonical.com lucid Release                                 
Hit http://ppa.launchpad.net lucid Release                                     
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US    
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg                     
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US  
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security/main Packages                    
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://us.archive.ubuntu.com lucid-backports Release.gpg                   
Hit http://packages.medibuntu.org lucid Release.gpg                            
Ign http://packages.medibuntu.org/ lucid/free Translation-en_US                
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
Hit http://security.ubuntu.com lucid-security/restricted Packages              
Hit http://security.ubuntu.com lucid-security/main Sources                     
Hit http://security.ubuntu.com lucid-security/restricted Sources               
Hit http://security.ubuntu.com lucid-security/universe Packages                
Hit http://archive.canonical.com lucid/partner Sources                         
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release                       
Hit http://us.archive.ubuntu.com lucid-updates Release               
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_US            
Hit http://packages.medibuntu.org lucid Release                                
Hit http://security.ubuntu.com lucid-security/universe Sources                 
Hit http://security.ubuntu.com lucid-security/multiverse Packages    
Hit http://security.ubuntu.com lucid-security/multiverse Sources     
Hit http://us.archive.ubuntu.com lucid-backports Release             
Hit http://packages.medibuntu.org lucid/free Packages                
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources            
Hit http://us.archive.ubuntu.com lucid/universe Packages             
Hit http://us.archive.ubuntu.com lucid/universe Sources              
Hit http://packages.medibuntu.org lucid/non-free Packages            
Hit http://ppa.launchpad.net lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-backports/main Packages
Hit http://us.archive.ubuntu.com lucid-backports/restricted Packages
Hit http://us.archive.ubuntu.com lucid-backports/universe Packages
Hit http://us.archive.ubuntu.com lucid-backports/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-backports/main Sources
Hit http://us.archive.ubuntu.com lucid-backports/restricted Sources
Hit http://us.archive.ubuntu.com lucid-backports/universe Sources
Hit http://us.archive.ubuntu.com lucid-backports/multiverse Sources
Reading package lists... Done

```

---

### Post by mc4man on 2010-05-03
> I went to the site and everything is there
The only lucid package  I see there is libcrystalhd1, and no doubt you'll find it available.
(to what purpose I'm not sure..


Edit: while you get an ign you probably will have this near it
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg

Anyway maybe this post will be of interest
[http://ubuntuforums.org/showthread.php?t=1470254](http://ubuntuforums.org/showthread.php?t=1470254)

---

### Post by nothingspecial on 2010-05-03
I don`t know if it does or should make a difference but every external repo I have added is in /etc/apt/sources.list.d

Where as the default repos are still in /etc/apt/sources.list

I **_wish_** they wouldn`t do that without telling you.

---

### Post by Sin@Sin-Sacrifice on 2010-05-03
Same here... perhapse I should try putting them there. Thanks everybody for the help.

@ mc4man : I thought I saw everything under the Lucid. I'll check again. That might just be it.  They had them for karmic a week before release. Oh well... soon enough.

---

### Post by Sin@Sin-Sacrifice on 2010-05-16
Turns out you have to use the svn repo. [http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu) lucid main

---

