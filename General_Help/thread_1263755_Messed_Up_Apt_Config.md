---
title: "Messed Up Apt Config"
date: 2009-09-11
forum: General Help
---

### Post by CarlosinFL on 2009-09-11
I seem to have a blank /etc/apt/source.list file and can't do any updates on my Ubuntu machines. Is there a way on the web I can copy and paste the original file in its place to start from scratch?

---

### Post by NoaHall on 2009-09-11
It's "/etc/apt/sources.list"

---

### Post by sisco311 on 2009-09-11
this is the default sources.list file for Jaunty:
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.                                    

deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.                                                
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in     
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.                                                                   
deb http://archive.ubuntu.com/ubuntu/ jaunty universe                      
deb-src http://archive.ubuntu.com/ubuntu/ jaunty universe                  
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe              
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates universe          

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in      
## multiverse WILL NOT receive any review or updates from the Ubuntu        
## security team.                                                           
deb http://archive.ubuntu.com/ubuntu/ jaunty multiverse                     
deb-src http://archive.ubuntu.com/ubuntu/ jaunty multiverse                 
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse             
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse         

## Uncomment the following two lines to add software from the 'backports'
## repository.                                                           
## N.B. software from this repository may not have been tested as        
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.                               
# deb http://cl.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://cl.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is 
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.                                                                
# deb http://archive.canonical.com/ubuntu jaunty partner                 
# deb-src http://archive.canonical.com/ubuntu jaunty partner             

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe           
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security universe       
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse         
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
```

---

