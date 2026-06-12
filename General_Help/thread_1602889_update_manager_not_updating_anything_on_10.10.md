---
title: "update manager not updating anything on 10.10"
date: 2010-10-22
forum: General Help
---

### Post by antonvrg on 2010-10-22
my update manager wont work. i click install and it does nothing.

how do i fix this?

video: [http://www.megaupload.com/?d=G28I1LPL](http://www.megaupload.com/?d=G28I1LPL)

---

### Post by TeoBigusGeekus on 2010-10-22
Open terminal and post us any error messages from
```
sudo apt-get update
```

---

### Post by antonvrg on 2010-10-23
> **TeoBigusGeekus said:**
> Open terminal and post us any error messages from
```
sudo apt-get update
```

none 

```
made2shred@made2shred-desktop:~$ sudo apt-get update
[sudo] password for made2shred: 
Hit http://au.archive.ubuntu.com maverick Release.gpg
Ign http://au.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Hit http://au.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_AU       
Ign http://au.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Hit http://au.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_AU 
Ign http://au.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Hit http://au.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_AU 
Ign http://au.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://au.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_AU   
Hit http://au.archive.ubuntu.com maverick-updates Release.gpg                  
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_AU
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_AU
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_AU
Hit http://au.archive.ubuntu.com maverick-proposed Release.gpg                 
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en 
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en_AU
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-proposed/multiverse Translation-en
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-proposed/multiverse Translation-en_AU
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-proposed/restricted Translation-en
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-proposed/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en_AU
Hit http://au.archive.ubuntu.com maverick Release                              
Hit http://au.archive.ubuntu.com maverick-updates Release                      
Hit http://au.archive.ubuntu.com maverick-proposed Release                     
Hit http://au.archive.ubuntu.com maverick/restricted Sources                   
Hit http://au.archive.ubuntu.com maverick/main Sources                         
Hit http://au.archive.ubuntu.com maverick/multiverse Sources                   
Hit http://au.archive.ubuntu.com maverick/universe Sources                     
Hit http://au.archive.ubuntu.com maverick/main i386 Packages                   
Hit http://au.archive.ubuntu.com maverick/restricted i386 Packages             
Hit http://apt.wakoopa.com all Release.gpg                                     
Ign http://apt.wakoopa.com/ all/main Translation-en                            
Ign http://apt.wakoopa.com/ all/main Translation-en_AU                         
Hit http://au.archive.ubuntu.com maverick/universe i386 Packages               
Hit http://au.archive.ubuntu.com maverick/multiverse i386 Packages             
Hit http://au.archive.ubuntu.com maverick-updates/restricted Sources           
Hit http://archive.canonical.com maverick Release.gpg                          
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Hit http://au.archive.ubuntu.com maverick-updates/main Sources                 
Hit http://au.archive.ubuntu.com maverick-updates/multiverse Sources           
Hit http://extras.ubuntu.com maverick Release.gpg                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Hit http://au.archive.ubuntu.com maverick-updates/universe Sources             
Hit http://au.archive.ubuntu.com maverick-updates/main i386 Packages           
Hit http://au.archive.ubuntu.com maverick-updates/restricted i386 Packages     
Hit http://winff.org lucid Release.gpg                                         
Ign http://winff.org/ubuntu/ lucid/universe Translation-en                     
Hit http://au.archive.ubuntu.com maverick-updates/universe i386 Packages       
Hit http://au.archive.ubuntu.com maverick-updates/multiverse i386 Packages     
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Hit http://au.archive.ubuntu.com maverick-proposed/restricted Sources          
Hit http://archive.ubuntu.com maverick Release.gpg                             
Hit http://au.archive.ubuntu.com maverick-proposed/main Sources                
Hit http://au.archive.ubuntu.com maverick-proposed/multiverse Sources          
Hit http://au.archive.ubuntu.com maverick-proposed/universe Sources            
Hit http://au.archive.ubuntu.com maverick-proposed/restricted i386 Packages    
Hit http://au.archive.ubuntu.com maverick-proposed/main i386 Packages          
Hit http://au.archive.ubuntu.com maverick-proposed/multiverse i386 Packages    
Hit http://au.archive.ubuntu.com maverick-proposed/universe i386 Packages      
Hit http://apt.wakoopa.com all Release                                         
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_AU    
Hit http://archive.canonical.com maverick Release                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_AU           
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://winff.org/ubuntu/ lucid/universe Translation-en_AU                  
Hit http://winff.org lucid Release                                             
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_AU
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_AU
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_AU
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_AU
Hit http://archive.ubuntu.com maverick Release                                 
Hit http://security.ubuntu.com maverick-security Release                       
Hit http://apt.wakoopa.com all/main i386 Packages                              
Hit http://archive.canonical.com maverick/partner Sources                      
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Hit http://winff.org lucid/universe i386 Packages                              
Hit http://archive.ubuntu.com maverick/main Sources                            
Hit http://security.ubuntu.com maverick-security/restricted Sources  
Hit http://archive.canonical.com maverick/partner i386 Packages
Hit http://archive.ubuntu.com maverick/restricted Sources
Hit http://security.ubuntu.com maverick-security/main Sources
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/universe Sources
Hit http://security.ubuntu.com maverick-security/main i386 Packages
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages
Hit http://security.ubuntu.com maverick-security/universe i386 Packages
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages
Reading package lists... Done
made2shred@made2shred-desktop:~$ 

```

---

### Post by Yumi on 2010-10-23
I have the same problem since about 2 month. Update-manager lists the packages to be updated, then it does nothing but refreshes the list. The update-manager also fails to check for updates automatically. In Lucid and early Maverick it checked regularly in the background and notified me when updates became available.

Manged to keep up to date as Synaptics-package-manager works! 

The terminal sudo apt-get update gives me a similar list antonvrg posts. When I look afterwards, no update has been done.

Tried to solve the problem ages ago through the Maverick forum but got no solution and hoped for the problem to go away, but it did not.

---

### Post by Hippytaff on 2010-10-23
Might be a bug...may be worth reporting it and having a look at this - [https://bugs.launchpad.net/ubuntu/+source/x11-xkb-utils/+bug/639933](https://bugs.launchpad.net/ubuntu/+source/x11-xkb-utils/+bug/639933)

similar issue with beta...might not be completely sorted yet!? :-)

---

### Post by mouchero08 on 2010-10-23
Slight different in 10.04 being run here but using the
sudo apt-get update
i eventually get
Sorry, try again.
sudo: 3 incorrect password attempts


update manager this 2 days has been like this nothing changed from the 20 times before i used the same password

---

### Post by Swagman on 2010-10-23
Here ya go

[** Click Me**](http://www.youtube.com/watch?v=iaX9qiQMbhg)

Boost the quality to see cleary.

---

### Post by sikander3786 on 2010-10-23
> **mouchero08 said:**
> Slight different in 10.04 being run here but using the
sudo apt-get update
i eventually get
Sorry, try again.
sudo: 3 incorrect password attempts


update manager this 2 days has been like this nothing changed from the 20 times before i used the same password
Are you sure you are typing the correct password. It doesn't show any asterisk, just go on typing it and hit Enter when finished.

---

### Post by antonvrg on 2010-10-23
> **Swagman said:**
> Here ya go

[** Click Me**](http://www.youtube.com/watch?v=iaX9qiQMbhg)

Boost the quality to see cleary.


my settings are the same. still nothing updating.

how do i update stuff in synaptic?

---

### Post by Yumi on 2010-10-23
Open Synaptic-package-manager. On the left select **Installed (upgradable)**. It now shows only those packages for which updates are available.

Then on top **Mark all Upgrades** and finally **Apply**. Done

---

### Post by dcstar on 2010-10-23
> **antonvrg said:**
> none 

```
made2shred@made2shred-desktop:~$ sudo apt-get update
[sudo] password for made2shred: 
Hit http://au.archive.ubuntu.com maverick Release.gpg
.......
Hit http://**au.archive.ubuntu.com** maverick Release                              
........ 

```

Never just use the default repository for a location, that will be hammered by thousands of others and may be behind in being updated because of the workload, manually select another mirror repository close to you.

---

