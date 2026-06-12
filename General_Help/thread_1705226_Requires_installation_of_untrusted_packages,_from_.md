---
title: "Requires installation of untrusted packages, from the USC"
date: 2011-03-11
forum: General Help
---

### Post by hunterkasy on 2011-03-11
I am running ubuntu 10.10 (64) I wanted to install a game from the USC

The game I was trying to install is: Micropolis, when I click on install and enter my password I get this message:  Requires installation of untrusted packages:::::The action would require the installation of packages from not authenticated sources.::::::libmikmod2 libsdl-mixer1.2 libsmpeg0 micropolis micropolis-data



I don;t know enough to fix it and install the game

all help I would appreciate

---

### Post by Krytarik on 2011-03-11
Please enter the following command in a terminal and post errors here, if you get any:
```
sudo apt-get update
```

---

### Post by hunterkasy on 2011-03-12
> **Krytarik said:**
> Please enter the following command in a terminal and post errors here, if you get any:
```
sudo apt-get update
```

user1@user1-Toshiba:~$ sudo apt-get update
[sudo] password for user1: 
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg [198B]                 
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable/main Translation-en           
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [72B]                      
Hit [http://deb.torproject.org](http://deb.torproject.org) experimental-lucid Release.gpg                   
Ign [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Ign [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable/main Translation-en_US        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US       
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US    
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en_US
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [1,338B]                             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://deb.torproject.org/torproject.org/](http://deb.torproject.org/torproject.org/) experimental-lucid/main Translation-en
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) maverick-getdeb/apps Translation-en      
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US 
Ign [http://deb.torproject.org/torproject.org/](http://deb.torproject.org/torproject.org/) experimental-lucid/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Get:5 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [474B]                   
Hit [http://deb.torproject.org](http://deb.torproject.org) experimental-lucid Release                       
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) maverick-getdeb/apps Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://deb.torproject.org](http://deb.torproject.org) experimental-lucid/main amd64 Packages 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US   
Ign [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb Release                          
Ign [http://deb.torproject.org](http://deb.torproject.org) experimental-lucid/main amd64 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg                  
Hit [http://deb.torproject.org](http://deb.torproject.org) experimental-lucid/main amd64 Packages           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main amd64 Packages 
Ign [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb/apps amd64 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted amd64 Packages
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe amd64 Packages       
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse amd64 Packages     
Ign [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb/apps amd64 Packages
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb/apps amd64 Packages
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports Release.gpg
Err [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb/apps amd64 Packages             
  504  Gateway Time-out
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted amd64 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe amd64 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse amd64 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/main amd64 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/restricted amd64 Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/universe amd64 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/multiverse amd64 Packages  
Fetched 2,279B in 7s (314B/s)                                                  
W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/apps/binary-amd64/Packages.gz](http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/apps/binary-amd64/Packages.gz)  504  Gateway Time-out

E: Some index files failed to download, they have been ignored, or old ones used instead.
user1@user1-Toshiba:~$

---

### Post by hunterkasy on 2011-03-12
I got the game to download and install in the USC by going to settings in update manager and I clicked on other software tab and deselected:

[http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu)

and by deselecting getdeb it works now

---

