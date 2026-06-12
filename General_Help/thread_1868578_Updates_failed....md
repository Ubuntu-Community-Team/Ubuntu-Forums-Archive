---
title: "Updates failed..."
date: 2011-10-24
forum: General Help
---

### Post by galacticaboy on 2011-10-24
So I like to manually update in the terminal via
```
sudo apt-get update
```
when I did that, I got this:
```
Err http://ppa.launchpad.net oneiric/main Sources                              
  404  Not Found
Err http://ppa.launchpad.net oneiric/main i386 Packages                        
  404  Not Found

```

Why is that?

---

### Post by TeoBigusGeekus on 2011-10-24
Your update server could be down or having problems.
Have you tried changing it?

---

### Post by rp3 on 2011-10-24
> **galacticaboy said:**
> So I like to manually update in the terminal via
```
sudo apt-get update
```
when I did that, I got this:
```
Err http://ppa.launchpad.net oneiric/main Sources                              
  404  Not Found
Err http://ppa.launchpad.net oneiric/main i386 Packages                        
  404  Not Found

```

Why is that?

I get the same thing, been like this for a week or so since the upgrade?

```
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                                   
  404  Not Found
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                                   
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages              
  404  Not Found
```

I think it's something bigger but not sure where to check?  After just browsing to ppa.launchpad.net there isn't a oneiric directory?

---

### Post by galacticaboy on 2011-10-25
Hmm, I do not like this one bit.

---

### Post by cryptotheslow on 2011-10-25
Hmm....

I can browse to 
[http://ppa.launchpad.net](http://ppa.launchpad.net)

but not:
[http://ppa.launchpad.net/oneiric/main](http://ppa.launchpad.net/oneiric/main)  (gives a 404 error)

Although I'm not sure that is actually the correct way to construct the url anyway!

There certainly isn't a lucid or maverick folder there either so I guess that is wrong!

Can you post up the output of:

```
cat /etc/apt/sources.list
```

Give me a few minutes and I'll fire up an 11.10 Live session and see what is setup as sources as standard.

---

### Post by cryptotheslow on 2011-10-25
OK - decided to install it in a VirtualBox instead so took a little longer :D

1st can you try:
Open Update Manager
Goto the Ubuntu Software Tab
Use the "Download from:" dropdown and select Other...
On the Choose a Download Server try the Select Best Server button or simply select a specific server geographically close to you. Then enter your password when prompted to save changes.
Then re-try your updates.

I'm in the UK - so this is what my sources.list looks like on a new install:
```
crypto@vbubu1110desk32:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://gb.archive.ubuntu.com/ubuntu/ oneiric-security main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric-security main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric-security universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric-security universe
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric-security multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main

```

Hope some of that helps! :)

---

### Post by galacticaboy on 2011-10-25
```
cat /etc/apt/david@david10:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu-Netbook 10.04 _Lucid Lynx_ - Release i386 (20100429.4)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ oneiric main restricted
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ oneiric restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ oneiric-updates main restricted
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ oneiric-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ oneiric universe
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ oneiric multiverse
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ oneiric-security main restricted
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ oneiric-security restricted main multiverse universe #Added by software-properties
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ oneiric-security universe
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ oneiric-security multiverse
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ oneiric-proposed restricted main multiverse universe
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ oneiric-proposed restricted main multiverse universe #Added by software-properties
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ oneiric-backports restricted main multiverse universe
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ oneiric-backports restricted main multiverse universe #Added by software-properties
deb http://extras.ubuntu.com/ubuntu oneiric main #Third party developers repository
david@david10:~$ 

```

---

### Post by cryptotheslow on 2011-10-25
Try choosing a different server as per my previous post :)

---

### Post by galacticaboy on 2011-10-25
> **cryptotheslow said:**
> Try choosing a different server as per my previous post :)

Did that, still says the same thing.

---

### Post by rp3 on 2011-10-26
[QUOTE=cryptotheslow;11391052]OK - decided to install it in a VirtualBox instead so took a little longer :D

1st can you try:
Open Update Manager
Goto the Ubuntu Software Tab
Use the "Download from:" dropdown and select Other...
On the Choose a Download Server try the Select Best Server button or simply select a specific server geographically close to you. Then enter your password when prompted to save changes.
Then re-try your updates.

I'm in the UK - so this is what my sources.list looks like on a new install:
[Quote]

Yup no help for me either.. :(

---

### Post by galacticaboy on 2011-10-26
I am at a loss, will this effect my PC when updates come out?

---

### Post by raja.genupula on 2011-10-26
[COLOR="DarkOrange"]hey do this 
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```


 I hope this will solve your issue

all the best. 
[/COLOR]

---

### Post by jmaque on 2011-10-26
> **raja.genupula said:**
> [COLOR="DarkOrange"]hey do this 
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```


 I hope this will solve your issue

all the best. 
[/COLOR]

I tried this on my system and I still get the same results.

---

### Post by galacticaboy on 2011-10-27
> **raja.genupula said:**
> [COLOR="DarkOrange"]hey do this 
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```


 I hope this will solve your issue

all the best. 
[/COLOR]

Nope it did nothing.

---

### Post by raja.genupula on 2011-10-27
> **galacticaboy said:**
> Nope it did nothing.

give me complete 
sudo apt-get update

---

### Post by Silent Warrior on 2011-10-27
[Ergh, never post before you read... This had all been said before.]

---

### Post by galacticaboy on 2011-10-27
> **raja.genupula said:**
> give me complete 
sudo apt-get update

```
david@david10:~$ sudo apt-get update
[sudo] password for david: 
Ign http://mirror.cc.columbia.edu oneiric InRelease
Ign http://mirror.cc.columbia.edu oneiric-updates InRelease                    
Ign http://mirror.cc.columbia.edu oneiric-security InRelease                   
Ign http://mirror.cc.columbia.edu oneiric-proposed InRelease                   
Ign http://mirror.cc.columbia.edu oneiric-backports InRelease                  
Ign http://dl.google.com stable InRelease                                      
Hit http://mirror.cc.columbia.edu oneiric Release.gpg                          
Hit http://mirror.cc.columbia.edu oneiric-updates Release.gpg                  
Hit http://mirror.cc.columbia.edu oneiric-security Release.gpg                 
Get:1 http://mirror.cc.columbia.edu oneiric-proposed Release.gpg [198 B]       
Hit http://mirror.cc.columbia.edu oneiric-backports Release.gpg                
Get:2 http://dl.google.com stable Release.gpg [198 B]                          
Hit http://mirror.cc.columbia.edu oneiric Release                              
Hit http://mirror.cc.columbia.edu oneiric-updates Release                      
Hit http://mirror.cc.columbia.edu oneiric-security Release                     
Get:3 http://mirror.cc.columbia.edu oneiric-proposed Release [32.4 kB]         
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://extras.ubuntu.com oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Get:4 http://dl.google.com stable Release [1,347 B]                            
Hit http://mirror.cc.columbia.edu oneiric-backports Release                    
Hit http://archive.canonical.com oneiric Release.gpg                           
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                      
Hit http://archive.canonical.com oneiric Release                               
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                         
Hit http://mirror.cc.columbia.edu oneiric/restricted Sources         
Hit http://mirror.cc.columbia.edu oneiric/main Sources
Hit http://mirror.cc.columbia.edu oneiric/multiverse Sources
Hit http://mirror.cc.columbia.edu oneiric/universe Sources
Hit http://mirror.cc.columbia.edu oneiric/main i386 Packages
Hit http://mirror.cc.columbia.edu oneiric/restricted i386 Packages
Hit http://mirror.cc.columbia.edu oneiric/universe i386 Packages
Hit http://mirror.cc.columbia.edu oneiric/multiverse i386 Packages
Hit http://mirror.cc.columbia.edu oneiric/main TranslationIndex
Hit http://mirror.cc.columbia.edu oneiric/multiverse TranslationIndex
Hit http://mirror.cc.columbia.edu oneiric/restricted TranslationIndex
Hit http://mirror.cc.columbia.edu oneiric/universe TranslationIndex
Hit http://mirror.cc.columbia.edu oneiric-updates/restricted Sources
Hit http://mirror.cc.columbia.edu oneiric-updates/main Sources
Hit http://mirror.cc.columbia.edu oneiric-updates/multiverse Sources
Hit http://mirror.cc.columbia.edu oneiric-updates/universe Sources
Hit http://mirror.cc.columbia.edu oneiric-updates/main i386 Packages
Hit http://mirror.cc.columbia.edu oneiric-updates/restricted i386 Packages
Hit http://mirror.cc.columbia.edu oneiric-updates/universe i386 Packages
Hit http://mirror.cc.columbia.edu oneiric-updates/multiverse i386 Packages
Hit http://mirror.cc.columbia.edu oneiric-updates/main TranslationIndex
Hit http://mirror.cc.columbia.edu oneiric-updates/multiverse TranslationIndex
Hit http://mirror.cc.columbia.edu oneiric-updates/restricted TranslationIndex
Hit http://mirror.cc.columbia.edu oneiric-updates/universe TranslationIndex
Hit http://mirror.cc.columbia.edu oneiric-security/restricted Sources 
Hit http://mirror.cc.columbia.edu oneiric-security/main Sources       
Hit http://mirror.cc.columbia.edu oneiric-security/multiverse Sources 
Hit http://mirror.cc.columbia.edu oneiric-security/universe Sources   
Hit http://mirror.cc.columbia.edu oneiric-security/main i386 Packages
Hit http://mirror.cc.columbia.edu oneiric-security/restricted i386 Packages
Hit http://mirror.cc.columbia.edu oneiric-security/universe i386 Packages
Hit http://mirror.cc.columbia.edu oneiric-security/multiverse i386 Packages
Hit http://mirror.cc.columbia.edu oneiric-security/main TranslationIndex
Hit http://mirror.cc.columbia.edu oneiric-security/multiverse TranslationIndex
Hit http://mirror.cc.columbia.edu oneiric-security/restricted TranslationIndex
Hit http://mirror.cc.columbia.edu oneiric-security/universe TranslationIndex
Get:5 http://mirror.cc.columbia.edu oneiric-proposed/restricted Sources [1,345 B]
Get:6 http://mirror.cc.columbia.edu oneiric-proposed/main Sources [63.7 kB]    
Get:7 http://mirror.cc.columbia.edu oneiric-proposed/multiverse Sources [14 B] 
Get:8 http://mirror.cc.columbia.edu oneiric-proposed/universe Sources [7,850 B]
Hit http://archive.canonical.com oneiric/partner Sources                       
Get:9 http://mirror.cc.columbia.edu oneiric-proposed/restricted i386 Packages [2,878 B]
Get:10 http://mirror.cc.columbia.edu oneiric-proposed/main i386 Packages [146 kB]
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Hit http://ppa.launchpad.net oneiric/main Sources                              
Get:11 http://mirror.cc.columbia.edu oneiric-proposed/multiverse i386 Packages [14 B]
Get:12 http://mirror.cc.columbia.edu oneiric-proposed/universe i386 Packages [17.1 kB]
Get:13 http://mirror.cc.columbia.edu oneiric-proposed/main TranslationIndex [73 B]
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Get:14 http://mirror.cc.columbia.edu oneiric-proposed/multiverse TranslationIndex [70 B]
Get:15 http://mirror.cc.columbia.edu oneiric-proposed/restricted TranslationIndex [71 B]
Get:16 http://mirror.cc.columbia.edu oneiric-proposed/universe TranslationIndex [73 B]
Hit http://mirror.cc.columbia.edu oneiric/main Translation-en                  
Hit http://mirror.cc.columbia.edu oneiric/multiverse Translation-en            
Hit http://mirror.cc.columbia.edu oneiric/restricted Translation-en            
Hit http://mirror.cc.columbia.edu oneiric/universe Translation-en              
Hit http://mirror.cc.columbia.edu oneiric-backports/restricted Sources         
Hit http://mirror.cc.columbia.edu oneiric-backports/main Sources               
Hit http://mirror.cc.columbia.edu oneiric-backports/multiverse Sources         
Hit http://mirror.cc.columbia.edu oneiric-backports/universe Sources           
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://mirror.cc.columbia.edu oneiric-backports/restricted i386 Packages   
Hit http://mirror.cc.columbia.edu oneiric-backports/main i386 Packages         
Hit http://mirror.cc.columbia.edu oneiric-backports/multiverse i386 Packages   
Hit http://mirror.cc.columbia.edu oneiric-backports/universe i386 Packages     
Hit http://mirror.cc.columbia.edu oneiric-backports/main TranslationIndex      
Hit http://mirror.cc.columbia.edu oneiric-backports/multiverse TranslationIndex
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://mirror.cc.columbia.edu oneiric-backports/restricted TranslationIndex
Hit http://mirror.cc.columbia.edu oneiric-backports/universe TranslationIndex  
Hit http://mirror.cc.columbia.edu oneiric-updates/main Translation-en          
Hit http://mirror.cc.columbia.edu oneiric-updates/multiverse Translation-en    
Hit http://mirror.cc.columbia.edu oneiric-updates/restricted Translation-en    
Hit http://mirror.cc.columbia.edu oneiric-updates/universe Translation-en      
Hit http://mirror.cc.columbia.edu oneiric-security/main Translation-en         
Hit http://mirror.cc.columbia.edu oneiric-security/multiverse Translation-en   
Hit http://mirror.cc.columbia.edu oneiric-security/restricted Translation-en   
Hit http://mirror.cc.columbia.edu oneiric-security/universe Translation-en     
Get:17 http://mirror.cc.columbia.edu oneiric-proposed/main Translation-en [47.4 kB]
Hit http://mirror.cc.columbia.edu oneiric-proposed/multiverse Translation-en   
Hit http://mirror.cc.columbia.edu oneiric-proposed/restricted Translation-en   
Get:18 http://mirror.cc.columbia.edu oneiric-proposed/universe Translation-en [11.5 kB]
Hit http://mirror.cc.columbia.edu oneiric-backports/main Translation-en        
Hit http://mirror.cc.columbia.edu oneiric-backports/multiverse Translation-en  
Hit http://mirror.cc.columbia.edu oneiric-backports/restricted Translation-en  
Hit http://mirror.cc.columbia.edu oneiric-backports/universe Translation-en    
Get:19 http://dl.google.com stable/main i386 Packages [779 B]                  
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://archive.canonical.com oneiric/partner Translation-en_US             
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en_US          
Ign http://archive.canonical.com oneiric/partner Translation-en      
Ign http://extras.ubuntu.com oneiric/main Translation-en             
Ign http://ppa.launchpad.net oneiric/main Translation-en             
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Fetched 333 kB in 8s (39.5 kB/s)                                               
Reading package lists... Done
david@david10:~$ 

```

Nevermind, now it works, I did not do anything... =-\

---

### Post by raja.genupula on 2011-10-27
> **galacticaboy said:**
> ```
david@david10:~$ sudo apt-get update
[sudo] password for david: 
Ign http://mirror.cc.columbia.edu oneiric InRelease
Ign http://mirror.cc.columbia.edu oneiric-updates InRelease                    
Ign http://mirror.cc.columbia.edu oneiric-security InRelease                   
Ign http://mirror.cc.columbia.edu oneiric-proposed InRelease                   
Ign http://mirror.cc.columbia.edu oneiric-backports InRelease                  
Ign http://dl.google.com stable InRelease                                      
Hit http://mirror.cc.columbia.edu oneiric Release.gpg                          
Hit http://mirror.cc.columbia.edu oneiric-updates Release.gpg                  
Hit http://mirror.cc.columbia.edu oneiric-security Release.gpg                 
Get:1 http://mirror.cc.columbia.edu oneiric-proposed Release.gpg [198 B]       
Hit http://mirror.cc.columbia.edu oneiric-backports Release.gpg                
Get:2 http://dl.google.com stable Release.gpg [198 B]                          
Hit http://mirror.cc.columbia.edu oneiric Release                              
Hit http://mirror.cc.columbia.edu oneiric-updates Release                      
Hit http://mirror.cc.columbia.edu oneiric-security Release                     
Get:3 http://mirror.cc.columbia.edu oneiric-proposed Release [32.4 kB]         
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://extras.ubuntu.com oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Get:4 http://dl.google.com stable Release [1,347 B]                            
Hit http://mirror.cc.columbia.edu oneiric-backports Release                    
Hit http://archive.canonical.com oneiric Release.gpg                           
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                      
Hit http://archive.canonical.com oneiric Release                               
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                         
Hit http://mirror.cc.columbia.edu oneiric/restricted Sources         
Hit http://mirror.cc.columbia.edu oneiric/main Sources
Hit http://mirror.cc.columbia.edu oneiric/multiverse Sources
Hit http://mirror.cc.columbia.edu oneiric/universe Sources
Hit http://mirror.cc.columbia.edu oneiric/main i386 Packages
Hit http://mirror.cc.columbia.edu oneiric/restricted i386 Packages
Hit http://mirror.cc.columbia.edu oneiric/universe i386 Packages
Hit http://mirror.cc.columbia.edu oneiric/multiverse i386 Packages
Hit http://mirror.cc.columbia.edu oneiric/main TranslationIndex
Hit http://mirror.cc.columbia.edu oneiric/multiverse TranslationIndex
Hit http://mirror.cc.columbia.edu oneiric/restricted TranslationIndex
Hit http://mirror.cc.columbia.edu oneiric/universe TranslationIndex
Hit http://mirror.cc.columbia.edu oneiric-updates/restricted Sources
Hit http://mirror.cc.columbia.edu oneiric-updates/main Sources
Hit http://mirror.cc.columbia.edu oneiric-updates/multiverse Sources
Hit http://mirror.cc.columbia.edu oneiric-updates/universe Sources
Hit http://mirror.cc.columbia.edu oneiric-updates/main i386 Packages
Hit http://mirror.cc.columbia.edu oneiric-updates/restricted i386 Packages
Hit http://mirror.cc.columbia.edu oneiric-updates/universe i386 Packages
Hit http://mirror.cc.columbia.edu oneiric-updates/multiverse i386 Packages
Hit http://mirror.cc.columbia.edu oneiric-updates/main TranslationIndex
Hit http://mirror.cc.columbia.edu oneiric-updates/multiverse TranslationIndex
Hit http://mirror.cc.columbia.edu oneiric-updates/restricted TranslationIndex
Hit http://mirror.cc.columbia.edu oneiric-updates/universe TranslationIndex
Hit http://mirror.cc.columbia.edu oneiric-security/restricted Sources 
Hit http://mirror.cc.columbia.edu oneiric-security/main Sources       
Hit http://mirror.cc.columbia.edu oneiric-security/multiverse Sources 
Hit http://mirror.cc.columbia.edu oneiric-security/universe Sources   
Hit http://mirror.cc.columbia.edu oneiric-security/main i386 Packages
Hit http://mirror.cc.columbia.edu oneiric-security/restricted i386 Packages
Hit http://mirror.cc.columbia.edu oneiric-security/universe i386 Packages
Hit http://mirror.cc.columbia.edu oneiric-security/multiverse i386 Packages
Hit http://mirror.cc.columbia.edu oneiric-security/main TranslationIndex
Hit http://mirror.cc.columbia.edu oneiric-security/multiverse TranslationIndex
Hit http://mirror.cc.columbia.edu oneiric-security/restricted TranslationIndex
Hit http://mirror.cc.columbia.edu oneiric-security/universe TranslationIndex
Get:5 http://mirror.cc.columbia.edu oneiric-proposed/restricted Sources [1,345 B]
Get:6 http://mirror.cc.columbia.edu oneiric-proposed/main Sources [63.7 kB]    
Get:7 http://mirror.cc.columbia.edu oneiric-proposed/multiverse Sources [14 B] 
Get:8 http://mirror.cc.columbia.edu oneiric-proposed/universe Sources [7,850 B]
Hit http://archive.canonical.com oneiric/partner Sources                       
Get:9 http://mirror.cc.columbia.edu oneiric-proposed/restricted i386 Packages [2,878 B]
Get:10 http://mirror.cc.columbia.edu oneiric-proposed/main i386 Packages [146 kB]
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Hit http://ppa.launchpad.net oneiric/main Sources                              
Get:11 http://mirror.cc.columbia.edu oneiric-proposed/multiverse i386 Packages [14 B]
Get:12 http://mirror.cc.columbia.edu oneiric-proposed/universe i386 Packages [17.1 kB]
Get:13 http://mirror.cc.columbia.edu oneiric-proposed/main TranslationIndex [73 B]
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Get:14 http://mirror.cc.columbia.edu oneiric-proposed/multiverse TranslationIndex [70 B]
Get:15 http://mirror.cc.columbia.edu oneiric-proposed/restricted TranslationIndex [71 B]
Get:16 http://mirror.cc.columbia.edu oneiric-proposed/universe TranslationIndex [73 B]
Hit http://mirror.cc.columbia.edu oneiric/main Translation-en                  
Hit http://mirror.cc.columbia.edu oneiric/multiverse Translation-en            
Hit http://mirror.cc.columbia.edu oneiric/restricted Translation-en            
Hit http://mirror.cc.columbia.edu oneiric/universe Translation-en              
Hit http://mirror.cc.columbia.edu oneiric-backports/restricted Sources         
Hit http://mirror.cc.columbia.edu oneiric-backports/main Sources               
Hit http://mirror.cc.columbia.edu oneiric-backports/multiverse Sources         
Hit http://mirror.cc.columbia.edu oneiric-backports/universe Sources           
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://mirror.cc.columbia.edu oneiric-backports/restricted i386 Packages   
Hit http://mirror.cc.columbia.edu oneiric-backports/main i386 Packages         
Hit http://mirror.cc.columbia.edu oneiric-backports/multiverse i386 Packages   
Hit http://mirror.cc.columbia.edu oneiric-backports/universe i386 Packages     
Hit http://mirror.cc.columbia.edu oneiric-backports/main TranslationIndex      
Hit http://mirror.cc.columbia.edu oneiric-backports/multiverse TranslationIndex
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://mirror.cc.columbia.edu oneiric-backports/restricted TranslationIndex
Hit http://mirror.cc.columbia.edu oneiric-backports/universe TranslationIndex  
Hit http://mirror.cc.columbia.edu oneiric-updates/main Translation-en          
Hit http://mirror.cc.columbia.edu oneiric-updates/multiverse Translation-en    
Hit http://mirror.cc.columbia.edu oneiric-updates/restricted Translation-en    
Hit http://mirror.cc.columbia.edu oneiric-updates/universe Translation-en      
Hit http://mirror.cc.columbia.edu oneiric-security/main Translation-en         
Hit http://mirror.cc.columbia.edu oneiric-security/multiverse Translation-en   
Hit http://mirror.cc.columbia.edu oneiric-security/restricted Translation-en   
Hit http://mirror.cc.columbia.edu oneiric-security/universe Translation-en     
Get:17 http://mirror.cc.columbia.edu oneiric-proposed/main Translation-en [47.4 kB]
Hit http://mirror.cc.columbia.edu oneiric-proposed/multiverse Translation-en   
Hit http://mirror.cc.columbia.edu oneiric-proposed/restricted Translation-en   
Get:18 http://mirror.cc.columbia.edu oneiric-proposed/universe Translation-en [11.5 kB]
Hit http://mirror.cc.columbia.edu oneiric-backports/main Translation-en        
Hit http://mirror.cc.columbia.edu oneiric-backports/multiverse Translation-en  
Hit http://mirror.cc.columbia.edu oneiric-backports/restricted Translation-en  
Hit http://mirror.cc.columbia.edu oneiric-backports/universe Translation-en    
Get:19 http://dl.google.com stable/main i386 Packages [779 B]                  
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://archive.canonical.com oneiric/partner Translation-en_US             
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en_US          
Ign http://archive.canonical.com oneiric/partner Translation-en      
Ign http://extras.ubuntu.com oneiric/main Translation-en             
Ign http://ppa.launchpad.net oneiric/main Translation-en             
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Fetched 333 kB in 8s (39.5 kB/s)                                               
Reading package lists... Done
david@david10:~$ 

```

Nevermind, now it works, I did not do anything... =-\

I am glad that you have solved your issue . please mark your thread as solved from thread tools.

---

