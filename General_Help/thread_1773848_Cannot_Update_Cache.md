---
title: "Cannot Update Cache"
date: 2011-06-02
forum: General Help
---

### Post by Joseph Schwenker on 2011-06-02
I've been trying to update the cache using sudo apt-get update, but it keeps hitting for most of the repositories.

```
joseph@joseph:~$ sudo apt-get update
[sudo] password for joseph: 
Get:1 http://dl.google.com stable Release.gpg [198B]                           
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en          
Hit http://extras.ubuntu.com maverick Release.gpg                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_GB           
Hit http://archive.canonical.com maverick Release.gpg                          
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_GB    
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_GB
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_GB       
Hit http://us.archive.ubuntu.com maverick Release.gpg                          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Get:2 http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB [94.5kB]
Get:3 http://linux.toribash.com toribash/ Release.gpg [72B]                    
Ign http://linux.toribash.com/apt/ toribash/ Translation-en                    
Ign http://linux.toribash.com/apt/ toribash/ Translation-en_GB                 
Ign http://linux.toribash.com/apt/ toribash/ Translation-en_US                 
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Hit http://archive.canonical.com maverick Release                              
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Get:4 http://dl.google.com stable Release.gpg [197B]                           
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Get:5 http://linux.toribash.com toribash/ Release [1,548B]                     
Hit http://archive.canonical.com maverick/partner i386 Packages                
Hit http://security.ubuntu.com maverick-security Release                       
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en      
Hit http://security.ubuntu.com maverick-security/main Sources                  
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_GB   
Get:6 http://linux.toribash.com toribash/ Packages [1,068B]                    
Hit http://security.ubuntu.com maverick-security/restricted Sources            
Hit http://security.ubuntu.com maverick-security/universe Sources              
Hit http://security.ubuntu.com maverick-security/multiverse Sources            
Hit http://security.ubuntu.com maverick-security/main i386 Packages            
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_US   
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages      
Hit http://security.ubuntu.com maverick-security/universe i386 Packages        
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages      
Get:7 http://dl.google.com stable Release [1,351B]               
Get:8 http://dl.google.com stable Release [1,347B]                             
Get:9 http://dl.google.com stable/main i386 Packages [1,228B]                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Get:10 http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_GB [91.2kB]
Get:11 http://dl.google.com stable/main i386 Packages [764B]                   
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Get:12 http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB [2,332B]
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Get:13 http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_GB [32.0kB]
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US   
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_GB
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_GB
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_GB
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_GB
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release
Hit http://us.archive.ubuntu.com maverick-updates Release            
Hit http://us.archive.ubuntu.com maverick/main Sources               
Hit http://us.archive.ubuntu.com maverick/restricted Sources
Hit http://us.archive.ubuntu.com maverick/universe Sources
Hit http://us.archive.ubuntu.com maverick/multiverse Sources
Hit http://us.archive.ubuntu.com maverick/main i386 Packages
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/main Sources
Hit http://us.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://us.archive.ubuntu.com maverick-updates/universe Sources
Hit http://us.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://us.archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/and471/kazam-daily-stable/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/and471/kazam-daily-stable/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net/and471/kazam-daily-stable/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/cheleb/blender-svn/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/cheleb/blender-svn/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net/cheleb/blender-svn/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/docky-core/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/docky-core/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net/docky-core/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/elementaryart/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/elementaryart/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net/elementaryart/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/postler-dev/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/postler-dev/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net/postler-dev/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/sgringwe/beatbox/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/sgringwe/beatbox/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net/sgringwe/beatbox/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/synapse-core/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/synapse-core/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net/synapse-core/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/tracker-team/tracker-unstable/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tracker-team/tracker-unstable/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net/tracker-team/tracker-unstable/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick Release  
Hit http://ppa.launchpad.net maverick Release  
Hit http://ppa.launchpad.net maverick Release  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Fetched 228kB in 6s (33.1kB/s)                                                 
Reading package lists... Done
joseph@joseph:~$ 

```

I currently cannot add any new software from a third-party repository because of this. How can I fix this?

---

### Post by LowSky on 2011-06-02
Open synaptic then go to Settings > then Repositories. Go to Other software tab... delete duplicates. then from synaptic then reload, then in synatic click mark upgrades and apply, or from a terminal

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Joseph Schwenker on 2011-06-02
I'm not seeing any duplicates, other than repositories with the source code. I'm attaching a screenshot of all my repositories.

---

### Post by Joseph Schwenker on 2011-06-03
My repositories still won't update. bump

---

### Post by linuxinstalledfromhdd on 2011-06-03
your source.list looks great.

it must be something else.

install Ubuntu-tweak and see if you can add software through that.

---

### Post by Joseph Schwenker on 2011-06-03
> **linuxinstalledfromhdd said:**
> your source.list looks great.

it must be something else.

install Ubuntu-tweak and see if you can add software through that.

I have Python 2.6, but Ubuntu Tweak needs Python 2.7 or greater. And I have no way of adding a repository for Python.

---

### Post by Joseph Schwenker on 2011-06-06
bump

---

### Post by wildmanne39 on 2011-06-06
> **Joseph Schwenker said:**
> bump

Hi, try this command in a terminal.
```
sudo rm -r /var/lib/apt/lists/* -vf
```
```
sudo apt-get update
```

---

### Post by linuxinstalledfromhdd on 2011-06-06
> **Joseph Schwenker said:**
> I have Python 2.6, but Ubuntu Tweak needs Python 2.7 or greater. And I have no way of adding a repository for Python.
I'm not running 2.7, and it works great. 

Try this in your terminal:
```

sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak

```

---

### Post by Joseph Schwenker on 2011-06-06
> **wildmanne39 said:**
> Hi, try this command in a terminal.
```
sudo rm -r /var/lib/apt/lists/* -vf
```
```
sudo apt-get update
```

I tried that command, but as soon as I added another repository and tried to update, it hit most of the repositories.

---

### Post by wojox on 2011-06-06
It hit most of the repositories because the others are updated.

---

### Post by linuxinstalledfromhdd on 2011-06-06
Try going into Synaptic Package manager...  Settings >>> Repositories >> 

Changing "Download from" to a different server and hit reload.

---

### Post by Joseph Schwenker on 2011-06-07
Not sure if they were working before or not, but I just found out that the repository I was trying to add had no support for Maverick, only Natty. I tried adding that Ubuntu Tweak PPA, and it added and installed perfectly. Thanks for your help, guys.

---

### Post by anonymousdude on 2011-06-07
Noob question.  What does 'hit' mean?  I see that a lot too when I run apt-get update.

---

### Post by Irony on 2011-06-07
Untick all the 'other' repositories and then update.

---

