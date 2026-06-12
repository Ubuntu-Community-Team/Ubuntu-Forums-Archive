---
title: "Cannot Update Sources"
date: 2011-01-17
forum: General Help
---

### Post by sanchino on 2011-01-17
[FONT=Arial][SIZE=3]Hi everyone[/SIZE][/FONT][FONT=Arial][SIZE=3],

I'm having a horrible time when trying to update my Ubuntu Maverick repositories. I have the following ERROR:

root@XXXXXX :/home/XXXXXX# **sudo apt-get update**
Hit [http://mirrors.sohu.com](http://mirrors.sohu.com) maverick Release.gpg
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick/main Translation-en               
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick/main Translation-en_US            
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick/multiverse Translation-en         
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick/multiverse Translation-en_US      
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick/restricted Translation-en         
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick/restricted Translation-en_US      
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick/universe Translation-en           
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick/universe Translation-en_US        
Hit [http://mirrors.sohu.com](http://mirrors.sohu.com) maverick-updates Release.gpg                       
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-updates/deb-src Translation-en    
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-updates/deb-src Translation-en_US 
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-updates/http://archive.ubuntu.com/ubuntu/ Translation-en
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-updates/http://archive.ubuntu.com/ubuntu/ Translation-en_US
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-updates/main Translation-en       
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-updates/main Translation-en_US    
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-updates/maverick Translation-en   
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-updates/maverick Translation-en_US
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-updates/multiverse Translation-en 
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-updates/restricted Translation-en 
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-updates/universe Translation-en   
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://mirrors.sohu.com](http://mirrors.sohu.com) maverick-security Release.gpg                      
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-security/main Translation-en      
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-security/main Translation-en_US   
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-security/universe Translation-en  
Ign [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://mirrors.sohu.com](http://mirrors.sohu.com) maverick Release                                   
Hit [http://mirrors.sohu.com](http://mirrors.sohu.com) maverick-updates Release                           
Hit [http://mirrors.sohu.com](http://mirrors.sohu.com) maverick-security Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Hit [http://mirrors.sohu.com](http://mirrors.sohu.com) maverick/main Sources                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release.gpg                         
Hit [http://mirrors.sohu.com](http://mirrors.sohu.com) maverick/universe Sources                          
Hit [http://mirrors.sohu.com](http://mirrors.sohu.com) maverick/multiverse Sources                        
Hit [http://mirrors.sohu.com](http://mirrors.sohu.com) maverick/restricted Sources                        
Hit [http://mirrors.sohu.com](http://mirrors.sohu.com) maverick/main i386 Packages                        
Hit [http://mirrors.sohu.com](http://mirrors.sohu.com) maverick/restricted i386 Packages                  
Hit [http://mirrors.sohu.com](http://mirrors.sohu.com) maverick/universe i386 Packages                    
Hit [http://mirrors.sohu.com](http://mirrors.sohu.com) maverick/multiverse i386 Packages                  
Hit [http://mirrors.sohu.com](http://mirrors.sohu.com) maverick-updates/main Sources                      
Hit [http://mirrors.sohu.com](http://mirrors.sohu.com) maverick-updates/universe Sources                  
Hit [http://mirrors.sohu.com](http://mirrors.sohu.com) maverick-updates/multiverse Sources                
Hit [http://mirrors.sohu.com](http://mirrors.sohu.com) maverick-updates/restricted i386 Packages          
Hit [http://mirrors.sohu.com](http://mirrors.sohu.com) maverick-updates/main i386 Packages                
Hit [http://mirrors.sohu.com](http://mirrors.sohu.com) maverick-security/main Sources                     
Hit [http://mirrors.sohu.com](http://mirrors.sohu.com) maverick-security/universe Sources                 
Hit [http://mirrors.sohu.com](http://mirrors.sohu.com) maverick-security/multiverse Sources               
Hit [http://mirrors.sohu.com](http://mirrors.sohu.com) maverick-security/main i386 Packages               
Hit [http://mirrors.sohu.com](http://mirrors.sohu.com) maverick-security/restricted i386 Packages         
Hit [http://mirrors.sohu.com](http://mirrors.sohu.com) maverick-security/universe i386 Packages           
Hit [http://mirrors.sohu.com](http://mirrors.sohu.com) maverick-security/multiverse i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release                                 
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US    
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages      
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse Sources                      
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe Sources [4,179kB]            
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages [66.3kB] 
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en_US             
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en            
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages [1,655B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en_US         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release                             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free i386 Packages                  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages              
Fetched 4,247kB in 15s (279kB/s)                                               
[COLOR=Red]W: Failed to fetch [http://mirrors.sohu.com/ubuntu/dists/maverick-updates/Release](http://mirrors.sohu.com/ubuntu/dists/maverick-updates/Release)  Unable to find expected entry  maverick/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.[/COLOR] 

------------------------------------------------------------------------------------------

Here's my sources.list after **cat /etc/apt/sources.list**

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick main restricted
deb-src [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-updates restricted main maverick [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) deb-src
deb-src [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick universe
deb-src [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick universe
deb [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-updates universe
deb-src [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick multiverse
deb-src [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick multiverse
deb [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-updates multiverse
deb-src [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-security main restricted
deb-src [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-security main
deb [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-security universe
deb-src [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-security universe
deb [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-security multiverse
deb-src [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick free non-free
deb [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security restricted main multiverse main universe 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick main multiverse main universe
deb-src [http://mirrors.sohu.com/ubuntu/](http://mirrors.sohu.com/ubuntu/) maverick restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick restricted

-----------------------------------------------------------------------------------------

I will surely appreciate all help, and in case there's trouble with my list, I could accept suggestions and/or installing your (if similar to mine)

Thank you, and best to all...

Sanchino
[/SIZE][/FONT]

---

