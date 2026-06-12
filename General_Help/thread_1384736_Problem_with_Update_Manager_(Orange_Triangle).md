---
title: "Problem with Update Manager (Orange Triangle)"
date: 2010-01-18
forum: General Help
---

### Post by kako13 on 2010-01-18
Hi,

I'm getting an orange triangle in the task-bar related to the Update Manger.

My source list is pasted below and I had attached some screen shots. 

  ```

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security multiverse
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu karmic main
deb http://download.virtualbox.org/virtualbox/debian karmic non-free
deb http://download.skype.com/linux/repos/debian/ stable non-free
deb http://dl.google.com/linux/deb/ stable non-free main


```

Any way to solve this?

---

### Post by michy99 on 2010-01-18
What errors do you get when you run this in a terminal?```
sudo apt-get update
```

---

### Post by kako13 on 2010-01-18
> **michy99 said:**
> What errors do you get when you run this in a terminal?```
sudo apt-get update
```


```

kelvin@kelvin-desktop:~$ sudo apt-get update
[sudo] password for kelvin: 
Hit http://download.virtualbox.org karmic Release.gpg                          
Ign http://download.virtualbox.org karmic/non-free Translation-en_US           
Get:1 http://us.archive.ubuntu.com karmic Release.gpg [189B]                   
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US                 
Get:2 http://dl.google.com stable Release.gpg [189B]                           
Ign http://dl.google.com stable/non-free Translation-en_US                     
Ign http://download.skype.com stable Release.gpg                               
Hit http://archive.canonical.com karmic Release.gpg                            
Ign http://archive.canonical.com karmic/partner Translation-en_US              
Get:3 http://ppa.launchpad.net karmic Release.gpg [307B]                       
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://download.virtualbox.org karmic Release                              
Hit http://packages.medibuntu.org karmic Release.gpg                           
Ign http://packages.medibuntu.org karmic/free Translation-en_US                
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US             
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US           
Get:4 http://us.archive.ubuntu.com karmic-updates Release.gpg [189B]           
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US   
Get:5 http://dl.google.com stable Release [2,540B]                             
Ign http://download.skype.com stable/non-free Translation-en_US                
Hit http://archive.canonical.com karmic Release                                
Get:6 http://ppa.launchpad.net karmic Release.gpg [307B]                       
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Get:7 http://ppa.launchpad.net karmic Release.gpg [307B]                       
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Get:8 http://ppa.launchpad.net karmic Release.gpg [307B]                       
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Get:9 http://ppa.launchpad.net karmic Release.gpg [307B]                       
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://download.virtualbox.org karmic/non-free Packages                    
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US            
Get:10 http://us.archive.ubuntu.com karmic-security Release.gpg [189B]         
Ign http://us.archive.ubuntu.com karmic-security/main Translation-en_US        
Hit http://packages.medibuntu.org karmic Release                               
Ign http://us.archive.ubuntu.com karmic-security/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com karmic-security/universe Translation-en_US    
Ign http://us.archive.ubuntu.com karmic-security/multiverse Translation-en_US  
Hit http://us.archive.ubuntu.com karmic Release                                
Get:11 http://dl.google.com stable/non-free Packages [1,010B]                  
Ign http://download.skype.com stable Release                                   
Get:12 http://ppa.launchpad.net karmic Release.gpg [307B]                      
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://archive.canonical.com karmic/partner Packages                       
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://ppa.launchpad.net karmic Release                                                                      
Hit http://ppa.launchpad.net karmic Release                                                                                           
Hit http://ppa.launchpad.net karmic Release                                                                                           
Hit http://ppa.launchpad.net karmic Release                                                                                           
Hit http://packages.medibuntu.org karmic/free Packages                                                                                
Hit http://us.archive.ubuntu.com karmic-updates Release                                                          
Hit http://us.archive.ubuntu.com karmic-security Release                                                                              
Hit http://download.skype.com stable/non-free Packages                                                                                
Hit http://archive.canonical.com karmic/partner Sources                                                          
Hit http://ppa.launchpad.net karmic Release                                                                      
Hit http://packages.medibuntu.org karmic/non-free Packages                                                      
Hit http://packages.medibuntu.org karmic/free Sources                                      
Hit http://packages.medibuntu.org karmic/non-free Sources                                  
Hit http://us.archive.ubuntu.com karmic/main Packages                                      
Hit http://us.archive.ubuntu.com karmic/restricted Packages          
Hit http://us.archive.ubuntu.com karmic/main Sources                 
Hit http://us.archive.ubuntu.com karmic/restricted Sources           
Hit http://us.archive.ubuntu.com karmic/universe Packages            
Hit http://us.archive.ubuntu.com karmic/universe Sources             
Hit http://us.archive.ubuntu.com karmic/multiverse Packages          
Hit http://ppa.launchpad.net karmic/main Packages                    
Hit http://ppa.launchpad.net karmic/main Sources                     
Hit http://ppa.launchpad.net karmic/main Packages                    
Hit http://ppa.launchpad.net karmic/main Packages                    
Hit http://ppa.launchpad.net karmic/main Packages                    
Hit http://us.archive.ubuntu.com karmic/multiverse Sources           
Hit http://us.archive.ubuntu.com karmic-updates/main Packages        
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages  
Hit http://us.archive.ubuntu.com karmic-updates/main Sources         
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources   
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages    
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources     
Hit http://ppa.launchpad.net karmic/main Packages                    
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages  
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources   
Hit http://us.archive.ubuntu.com karmic-security/main Packages       
Hit http://us.archive.ubuntu.com karmic-security/restricted Packages 
Hit http://us.archive.ubuntu.com karmic-security/main Sources        
Hit http://us.archive.ubuntu.com karmic-security/restricted Sources  
Hit http://us.archive.ubuntu.com karmic-security/universe Packages   
Hit http://us.archive.ubuntu.com karmic-security/universe Sources    
Hit http://ppa.launchpad.net karmic/main Packages                    
Get:13 http://dl.google.com stable/main Packages [918B]              
Hit http://us.archive.ubuntu.com karmic-security/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-security/multiverse Sources
Fetched 7,066B in 5s (1,390B/s)
Reading package lists... Done


```

---

### Post by michy99 on 2010-01-18
That looks okay, so what do you get for this?```
sudo apt-get upgrade
```

---

### Post by kako13 on 2010-01-18
> **michy99 said:**
> That looks okay, so what do you get for this?```
sudo apt-get upgrade
```

```

kelvin@kelvin-desktop:~$ sudo apt-get upgrade
[sudo] password for kelvin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kelvin@kelvin-desktop:~$ ^C
kelvin@kelvin-desktop:~$

```

---

### Post by michy99 on 2010-01-18
So what happens now if you open the update manager? Is it still the same?

---

### Post by kako13 on 2010-01-18
> **michy99 said:**
> So what happens now if you open the update manager? Is it still the same?

Yes a lots of Failed in the status...

---

### Post by kako13 on 2010-01-19
Any idea? [-o<

---

### Post by kako13 on 2010-01-21
[-o<

---

### Post by michy99 on 2010-01-21
Can you post the 'failed' messages?

---

### Post by kako13 on 2010-01-21
> **michy99 said:**
> Can you post the 'failed' messages?

Hi,

I uploaded an screen-shoot.

---

### Post by steveneddy on 2010-01-21
The URL's are not showing in the pic - either make the window larger or use the scroll bar to show us the complete URL.

---

### Post by kako13 on 2010-01-21
> **steveneddy said:**
> The URL's are not showing in the pic - either make the window larger or use the scroll bar to show us the complete URL.

Sorry, now is way better.

---

### Post by john newbuntu on 2010-01-21
Not sure if archive/canonical was/is down .  But if you go to synaptic and choose settings->repositories->other software and uncheck all the boxes.  (Remember the ones that you have unchecked) Click close. Hit apply in synaptic.

Then do the "sudo apt-get update" a couple of times and see if that helps.

---

### Post by kako13 on 2010-01-22
> **john newbuntu said:**
> Not sure if archive/canonical was/is down .  But if you go to synaptic and choose settings->repositories->other software and uncheck all the boxes.  (Remember the ones that you have unchecked) Click close. Hit apply in synaptic.

Then do the "sudo apt-get update" a couple of times and see if that helps.

I did that but still the same problem.  I had attached a screenshoot.

---

