---
title: "xbmc ubuntu 11.10"
date: 2012-02-06
forum: General Help
---

### Post by macele on 2012-02-06
I've been trying to figure out how to install xbmc on ubuntu following the direction found here: [https://launchpad.net/~team-xbmc/+archive/ppa]("https://launchpad.net/~team-xbmc/+archive/ppa") I've followed the instructions as best I can. 

I did the

```
sudo add-apt-repository ppa:team-xbmc/ppa
sudo apt-get update
sudo apt-get install xbmc
```

and I get...

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for xbmc

```

I also tried...

> sudo apt-get build-dep xbmc

But i get the same response. Clearly I am doing something wrong. I have not been using linux that long, so if someone could help me I would be very appreciative.

---

### Post by sportfreak2020 on 2012-02-06
i would first check the sources list file to see if its in the right location .. 

you can search for it by typing

> sudo find / -name sources.list

mine is currently at /etc/apt/sources.list

anywho, if that is right, sometimes running 

> sudo apt-get -f install 

fixes broken stuff, and then after that run 

> sudo apt-get update
sudo apt-get upgrade 

let me know if that still dosent work ...

---

### Post by macele on 2012-02-06
Thanks for the reply sportfreak2020

I tried all of the things you said:

```
# sudo find / -name sources.list 
/etc/apt/sources.list
/usr/share/doc/apt/examples/sources.list

```

Seems fine

```
# sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
roger!

```
# sudo apt-get update
Ign http://archive.ubuntu.com oneiric InRelease
Ign http://extras.ubuntu.com oneiric InRelease                      
Ign http://ppa.launchpad.net oneiric InRelease                      
Ign http://us.archive.ubuntu.com oneiric InRelease                   
Ign http://us.archive.ubuntu.com oneiric-updates InRelease                                 
Ign http://us.archive.ubuntu.com oneiric-backports InRelease                               
Hit http://archive.ubuntu.com oneiric Release.gpg                                          
Hit http://extras.ubuntu.com oneiric Release.gpg                     
Hit http://ppa.launchpad.net oneiric Release.gpg                     
Ign http://us.archive.ubuntu.com oneiric-security InRelease          
Ign http://us.archive.ubuntu.com oneiric-proposed InRelease                                
Hit http://us.archive.ubuntu.com oneiric Release.gpg                                       
Hit http://archive.ubuntu.com oneiric Release                                              
Hit http://extras.ubuntu.com oneiric Release                                               
Hit http://ppa.launchpad.net oneiric Release                         
Hit http://us.archive.ubuntu.com oneiric-updates Release.gpg                                
Hit http://us.archive.ubuntu.com oneiric-backports Release.gpg                             
Hit http://us.archive.ubuntu.com oneiric-security Release.gpg                              
Hit http://archive.ubuntu.com oneiric/main Sources                                         
Hit http://extras.ubuntu.com oneiric/main Sources                    
Hit http://ppa.launchpad.net oneiric/main Sources                    
Hit http://us.archive.ubuntu.com oneiric-proposed Release.gpg        
Hit http://archive.ubuntu.com oneiric/restricted Sources                                   
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                                   
Hit http://extras.ubuntu.com oneiric/main i386 Packages              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages             
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://us.archive.ubuntu.com oneiric Release                     
Hit http://us.archive.ubuntu.com oneiric-updates Release                                    
Hit http://us.archive.ubuntu.com oneiric-backports Release                                  
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                                  
Hit http://us.archive.ubuntu.com oneiric-security Release            
Hit http://us.archive.ubuntu.com oneiric-proposed Release                                   
Hit http://us.archive.ubuntu.com oneiric/restricted Sources                                 
Hit http://us.archive.ubuntu.com oneiric/main Sources                                       
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources                                 
Hit http://us.archive.ubuntu.com oneiric/universe Sources                                   
Hit http://us.archive.ubuntu.com oneiric/main amd64 Packages                                
Hit http://us.archive.ubuntu.com oneiric/restricted amd64 Packages                          
Hit http://us.archive.ubuntu.com oneiric/universe amd64 Packages     
Hit http://us.archive.ubuntu.com oneiric/multiverse amd64 Packages   
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages          
Hit http://us.archive.ubuntu.com oneiric/restricted i386 Packages    
Hit http://us.archive.ubuntu.com oneiric/universe i386 Packages      
Hit http://us.archive.ubuntu.com oneiric/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex       
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex   
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Sources  
Hit http://us.archive.ubuntu.com oneiric-updates/main Sources        
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Sources  
Hit http://us.archive.ubuntu.com oneiric-updates/universe Sources    
Hit http://us.archive.ubuntu.com oneiric-updates/main amd64 Packages 
Hit http://us.archive.ubuntu.com oneiric-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/main i386 Packages  
Hit http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/main Sources      
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Sources
Hit http://us.archive.ubuntu.com oneiric-backports/universe Sources  
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-security/restricted Sources 
Hit http://us.archive.ubuntu.com oneiric-security/main Sources       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US          
Hit http://us.archive.ubuntu.com oneiric-security/multiverse Sources 
Hit http://us.archive.ubuntu.com oneiric-security/universe Sources   
Hit http://us.archive.ubuntu.com oneiric-security/main amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-security/restricted amd64 Packages
Ign http://extras.ubuntu.com oneiric/main Translation-en_US          
Hit http://us.archive.ubuntu.com oneiric-security/universe amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-security/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-security/main i386 Packages 
Hit http://us.archive.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric-security/universe i386 Packages
Ign http://ppa.launchpad.net oneiric/main Translation-en             
Ign http://extras.ubuntu.com oneiric/main Translation-en             
Hit http://us.archive.ubuntu.com oneiric-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric-security/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-security/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-proposed/restricted Sources
Hit http://us.archive.ubuntu.com oneiric-proposed/main Sources
Hit http://us.archive.ubuntu.com oneiric-proposed/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric-proposed/universe Sources
Hit http://us.archive.ubuntu.com oneiric-proposed/restricted amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-proposed/main amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-proposed/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-proposed/universe amd64 Packages
Hit http://us.archive.ubuntu.com oneiric-proposed/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric-proposed/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric-proposed/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric-proposed/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric-proposed/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-proposed/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-proposed/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-proposed/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/main Translation-en
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/universe Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/universe Translation-en
Hit http://us.archive.ubuntu.com oneiric-security/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-security/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-security/universe Translation-en
Hit http://us.archive.ubuntu.com oneiric-proposed/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-proposed/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-proposed/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-proposed/universe Translation-en
Reading package lists... Done

```
alrighty...

```
#sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
ok..

```
# sudo apt-get install xbmc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xbmc

```
Darn!

```
# sudo apt-get build-dep xbmc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for xbmc


```

Just seems like xbmc is no long in the apt database. *shurg*
Any ideas?

---

### Post by stinkeye on 2012-02-07
From what I can see there is no build of xbmc for oneiric in the team-xbmc ppa.
I have not tried but there is a solution [**_[COLOR="darkred"]HERE[/COLOR]_**]("http://www.ubuntugeek.com/how-to-install-xbmc-on-ubuntu-11-10-oneiric-using-ppa.html")
using a ppa where someone has built for 11.10.

---

### Post by HiImTye on 2012-02-07
```
sudo add-apt-repository ppa:team-xbmc/unstable
```
should do it. the regular team xbmc repos dont have any releases for 11.10 (and using 11.04 releases can potentially seriously damage your system)

---

### Post by macele on 2012-02-07
> **stinkeye said:**
> From what I can see there is no build of xbmc for oneiric in the team-xbmc ppa.
I have not tried but there is a solution [**_[COLOR="darkred"]HERE[/COLOR]_**]("http://www.ubuntugeek.com/how-to-install-xbmc-on-ubuntu-11-10-oneiric-using-ppa.html")
using a ppa where someone has built for 11.10.

Thanks. That fixed me up!

---

