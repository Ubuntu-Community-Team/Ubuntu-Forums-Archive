---
title: "Can't Update!!!"
date: 2011-12-15
forum: General Help
---

### Post by theindianofthegroup on 2011-12-15
I tried to install battery-status applet a week or so ago. It did not install properly and since then my system has been a little screwy...I am running ubuntu 11.10 on a Dell Inspiron Mini 910.

When I try to update I get these errors and it cancels the whole update:


adam@thegreat:~$ sudo apt-get update
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric InRelease                            
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                    
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free i386 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free TranslationIndex                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free TranslationIndex            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US   
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en      
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Translation-en
W: Failed to fetch [http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
adam@thegreat:~$

-Any help is much appreciated!!
--Alpha

---

### Post by seawolf167 on 2011-12-15
It looks like it can't find some of your ppa: If you know the correct address, you can edit this lines and correct them, else you can simply remove the lines which are failing by editing your sources.list file.

```
gedit /etc/apt/sources.list
```

Alternatively, you can generate a new sources.list file from [this website]("http://repogen.simplylinux.ch/"). If you follow this route, ensure you create a backup of your current sources.list file just incase

```
cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

To update the lists, then run

```
sudo apt-get update
```

and to upgrade, run

```
sudo apt-get upgrade
```

---

### Post by bluexrider on 2011-12-15
> **seawolf167 said:**
> It looks like it can't find some of your ppa: If you know the correct address, you can edit this lines and correct them, else you can simply remove the lines which are failing by editing your sources.list file.

```
gedit /etc/apt/sources.list
```Alternatively, you can generate a new sources.list file from [this website]("http://repogen.simplylinux.ch/"). If you follow this route, ensure you create a backup of your current sources.list file just incase

```
cp /etc/apt/sources.list /etc/apt/sources.list.backup
```To update the lists, then run

```
sudo apt-get update
```and to upgrade, run

```
sudo apt-get upgrade
```

if that doesn't work change your server in Software Sources to "Other" then "best server"

---

### Post by bluexrider on 2011-12-15
> **seawolf167 said:**
> It looks like it can't find some of your ppa: If you know the correct address, you can edit this lines and correct them, else you can simply remove the lines which are failing by editing your sources.list file.

```
gedit /etc/apt/sources.list
```Alternatively, you can generate a new sources.list file from [this website]("http://repogen.simplylinux.ch/"). If you follow this route, ensure you create a backup of your current sources.list file just incase
```
cp /etc/apt/sources.list /etc/apt/sources.list.backup
```To update the lists, then run
```
sudo apt-get update
```and to upgrade, run
```
sudo apt-get upgrade
```

if that doesn't work change your server in Software Sources to "Other" then "best server"

---

### Post by theindianofthegroup on 2011-12-28
ubuntu is turning me into more and more of a computer nerd, but i am still on the very novice side of the fence. when i generate my sources list this is what it is showing:

# deb cdrom:[Ubuntu-Netbook 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse



maybe it is just me, but i don't see any lines corresponding to the error i am getting. i dont want to tamper when i am unsure. can you tell which ones need to go?

---

### Post by plucky on 2011-12-29
> maybe it is just me, but i don't see any lines corresponding to the error i am getting. i dont want to tamper when i am unsure. can you tell which ones need to go? 


That is because PPA's are stored in /etc/apt/sources.list.d

What does ```
cat /etc/apt/sources.list.d/*.list
``` show you?

See [Here](http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/) shows no oneiric PPA.

Good luck

---

### Post by theindianofthegroup on 2012-01-08
adam@thegreat:~$ cat /etc/apt/sources.list.d/*.list
deb [http://ppa.launchpad.net/iaz/battery-status/ubuntu](http://ppa.launchpad.net/iaz/battery-status/ubuntu) oneiric main
deb-src [http://ppa.launchpad.net/iaz/battery-status/ubuntu](http://ppa.launchpad.net/iaz/battery-status/ubuntu) oneiric main
# deb [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) oneiric main # disabled on upgrade to oneiric
# deb-src [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) oneiric main # disabled on upgrade to oneiric
# deb [http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu](http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu) oneiric main # disabled on upgrade to oneiric
# deb-src [http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu](http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu) oneiric main # disabled on upgrade to oneiric
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) oneiric free non-free #Medibuntu - Ubuntu 11.10 "oneiric ocelot"
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) oneiric free non-free #Medibuntu (source) - Ubuntu 11.10 "oneiric ocelot"
# deb [http://ppa.launchpad.net/tsbarnes/indicator-keylock/ubuntu](http://ppa.launchpad.net/tsbarnes/indicator-keylock/ubuntu) oneiric main # disabled on upgrade to oneiric
# deb-src [http://ppa.launchpad.net/tsbarnes/indicator-keylock/ubuntu](http://ppa.launchpad.net/tsbarnes/indicator-keylock/ubuntu) oneiric main # disabled on upgrade to oneiric
# deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) oneiric main # disabled on upgrade to oneiric
# deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) oneiric main # disabled on upgrade to oneiric
# deb [http://ppa.launchpad.net/user/ppa-name/ubuntu](http://ppa.launchpad.net/user/ppa-name/ubuntu) oneiric main # disabled on upgrade to oneiric
# deb-src [http://ppa.launchpad.net/user/ppa-name/ubuntu](http://ppa.launchpad.net/user/ppa-name/ubuntu) oneiric main # disabled on upgrade to oneiric
deb [http://ppa.launchpad.net/vicox/syspeek/ubuntu](http://ppa.launchpad.net/vicox/syspeek/ubuntu) oneiric main
deb-src [http://ppa.launchpad.net/vicox/syspeek/ubuntu](http://ppa.launchpad.net/vicox/syspeek/ubuntu) oneiric main
deb [http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu](http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu) oneiric main
deb-src [http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu](http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu) oneiric main

---

### Post by plucky on 2012-01-08
```
deb http://ppa.launchpad.net/iaz/battery-status/ubuntu oneiric main
deb-src http://ppa.launchpad.net/iaz/battery-status/ubuntu oneiric main
```

Those two do not have repositories for oneiric,so delete them from your Software Sources.

See [Here](http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/)

Good Luck

---

