---
title: "Cannot update sources update manager"
date: 2010-01-05
forum: General Help
---

### Post by xxterry1xx on 2010-01-05
some reason i can't update my sources no matter how many servers i try to update it from it does not work i tryed alot of things like update manager and synaptic package manager and terminal to update but nothing is not working

Could not download all repository indexes
The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.


i can get on the internet fine but the update manager has not worked for 12 days


this is my /etc/apt/sources.list

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

---

### Post by zvacet on 2010-01-05
Your source list look good,but I will replace following lines

deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) karmic main restricted
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) karmic universe
 
with 

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic main restricted
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic universe

and see if that make any difference.

---

### Post by mikewhatever on 2010-01-05
Can you actually post the output of <sudo apt-get update>. Might also want to wrap CODE tags around the output to make the post more readable.

---

### Post by xxterry1xx on 2010-01-07
> **mikewhatever said:**
> Can you actually post the output of <sudo apt-get update>. Might also want to wrap CODE tags around the output to make the post more readable.  some reason it takes along time to update ubuntu has been updated around dec 20-24 but after iv never logged on to ubuntu in dec 28 or so i tryed to update and it did not work so i kept trying again each day and still not working

terry@Admin:~$ sudo -s
[sudo] password for terry: 
root@Admin:~# sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic Release.gpg                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                  
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/main Translation-en_CA               
40% [1 Translation-en_CA bzip2 0] [Connecting to 200.141.202.162 (200.141.202.1bzip2: (stdin) is not a bzip2 file.
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/main Translation-en_CA                 
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_CA              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_CA    
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/restricted Translation-en_CA         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_CA      
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/universe Translation-en_CA         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_CA    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages               
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/multiverse Translation-en_CA           
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates Release.gpg [189B]           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/main Translation-en_CA         
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages           
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/restricted Translation-en_CA   
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources          
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/universe Translation-en_CA     
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/multiverse Translation-en_CA   
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic Release                                
Get:11 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates Release [44.1kB]            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/main Packages                          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/restricted Packages                  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/main Sources                         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/restricted Sources                   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/universe Packages                    
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/universe Sources                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/multiverse Packages                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/multiverse Sources                     
Get:13 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/main Packages               
Get:14 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/restricted Packages         
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources           
Get:16 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/main Sources                
Get:17 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/restricted Sources          
Get:18 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/universe Packages           
Get:19 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/universe Sources            
99% [2 Translation-en_CA bzip2 0] [Connecting to 200.141.202.162 (200.141.202.1


idk why its taking along time but
its taking awhile so far that took 10 mins

---

### Post by xxterry1xx on 2010-01-07
> **zvacet said:**
> Your source list look good,but I will replace following lines

deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) karmic main restricted
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) karmic universe
 
with 

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic main restricted
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic universe

and see if that make any difference.
it did not work

---

### Post by xxterry1xx on 2010-01-10
> **xxterry1xx said:**
> it did not work

bump

---

### Post by lyall on 2010-01-10
have you check to see which server you are trying to connect to for the best connect from Software Soucres
from the download from: select other
then select the country you want to test and click on Select Best Server
mine tested 325 test sites to see which one had the best ping from.
it depends on the web usage at that time, which it can change from minute to minute.  

good luck and have fun learning

---

### Post by xxterry1xx on 2010-01-18
> **lyall said:**
> have you check to see which server you are trying to connect to for the best connect from Software Soucres
from the download from: select other
then select the country you want to test and click on Select Best Server
mine tested 325 test sites to see which one had the best ping from.
it depends on the web usage at that time, which it can change from minute to minute.  

good luck and have fun learning did not work

---

