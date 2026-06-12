---
title: "Some problem with the update"
date: 2011-07-13
forum: General Help
---

### Post by var1989 on 2011-07-13
Hi

When i gave 

sudo apt-get update 

this is what it shows

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.


Thanks in advance

---

### Post by Rubi1200 on 2011-07-13
Hi and welcome to the forums :-)

Open a terminal with Ctr+Alt+T and run the following commands (best to copy and paste to avoid mistakes):

```
sudo rm /var/lib/apt/lists/* -vf
```
this removes corrupted package lists

```
sudo apt-get update
```
this refreshes/updates the lists

Let us know if this works please.

---

### Post by Surendil on 2011-07-13
do you have the file sources.list in /etc/apt/ ?

---

### Post by var1989 on 2011-07-13
sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty InRelease                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                        
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]                        
Get:2 [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg [198 B]                   
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg [198 B]            
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates InRelease                       
Get:4 [http://archive.canonical.com](http://archive.canonical.com) natty Release [5,916 B]           
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release [9,753 B]                         
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release [27.2 kB]              
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner amd64 Packages                  
Get:7 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty Release.gpg [198 B]                   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Get:8 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates Release.gpg [198 B] 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                      
Get:9 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty Release [39.8 kB]           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main amd64 Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main amd64 Packages              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted amd64 Packages        
Get:10 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates Release [27.2 kB]            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe amd64 Packages          
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_IN               
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/main Sources                            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/universe Sources                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse amd64 Packages        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/main amd64 Packages                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/restricted amd64 Packages               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/universe amd64 Packages                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_IN                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/multiverse amd64 Packages               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/universe TranslationIndex               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/main Sources                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/restricted Sources              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/universe Sources                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/multiverse Sources              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/main amd64 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/restricted amd64 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/universe amd64 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/multiverse amd64 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/main TranslationIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/restricted TranslationIndex    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/universe TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_IN   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/main Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/universe Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/universe Translation-en
Fetched 111 kB in 46s (2,397 B/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by var1989 on 2011-07-13
Yeah i have the sources.lst in the /etc/apt

---

### Post by Surendil on 2011-07-13
comment the line "http://in.archive.ubuntu.com natty/main amd64 Packages"  in /etc/apt/sources.list and run apt-get update again

---

### Post by var1989 on 2011-07-13
cat sources.list
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

theres no line like  "http://in.archive.ubuntu.com natty/main amd64 Packages"   in the sources.list

---

### Post by var1989 on 2011-07-14
please help me out !

---

### Post by plucky on 2011-07-14
> **var1989 said:**
> please help me out !

Read post #2 in this thread by Rubi1200.

Good Luck

---

