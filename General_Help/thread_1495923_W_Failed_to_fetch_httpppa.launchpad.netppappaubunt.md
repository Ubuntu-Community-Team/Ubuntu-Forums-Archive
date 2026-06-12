---
title: "W: Failed to fetch http://ppa.launchpad.net/ppa/ppa/ubuntu/dists/karmic/main/binary-i"
date: 2010-05-28
forum: General Help
---

### Post by nomnex on 2010-05-28
Error message during update on Karmic (see 'Ign' lines, and the end of the block quote).

```
mt@fmv:~$ sudo apt-get update
Hit http://jp.archive.ubuntu.com karmic Release.gpg
Ign http://jp.archive.ubuntu.com karmic/main Translation-en_US                                 
Ign http://jp.archive.ubuntu.com karmic/restricted Translation-en_US                           
Ign http://jp.archive.ubuntu.com karmic/universe Translation-en_US                             
Ign http://jp.archive.ubuntu.com karmic/multiverse Translation-en_US                           
Hit http://jp.archive.ubuntu.com karmic-updates Release.gpg                                    
Ign http://jp.archive.ubuntu.com karmic-updates/main Translation-en_US                         
Ign http://jp.archive.ubuntu.com karmic-updates/restricted Translation-en_US                   
Ign http://jp.archive.ubuntu.com karmic-updates/universe Translation-en_US                     
Ign http://jp.archive.ubuntu.com karmic-updates/multiverse Translation-en_US                   
Hit http://jp.archive.ubuntu.com karmic-proposed Release.gpg                                   
Ign http://jp.archive.ubuntu.com karmic-proposed/restricted Translation-en_US                  
Ign http://jp.archive.ubuntu.com karmic-proposed/main Translation-en_US                        
Ign http://jp.archive.ubuntu.com karmic-proposed/multiverse Translation-en_US                  
Ign http://jp.archive.ubuntu.com karmic-proposed/universe Translation-en_US                    
Hit http://jp.archive.ubuntu.com karmic Release                                                
Hit http://jp.archive.ubuntu.com karmic-updates Release                                        
Hit http://jp.archive.ubuntu.com karmic-proposed Release                                       
Hit http://jp.archive.ubuntu.com karmic/main Packages                                          
Hit http://jp.archive.ubuntu.com karmic/restricted Packages                                    
Hit http://jp.archive.ubuntu.com karmic/universe Packages                                      
Hit http://jp.archive.ubuntu.com karmic/multiverse Packages                                    
Hit http://jp.archive.ubuntu.com karmic-updates/main Packages                                  
Hit http://jp.archive.ubuntu.com karmic-updates/restricted Packages                            
Hit http://jp.archive.ubuntu.com karmic-updates/universe Packages                              
Hit http://jp.archive.ubuntu.com karmic-updates/multiverse Packages                            
Hit http://jp.archive.ubuntu.com karmic-proposed/restricted Packages                           
Hit http://jp.archive.ubuntu.com karmic-proposed/main Packages                                 
Hit http://jp.archive.ubuntu.com karmic-proposed/multiverse Packages                           
Hit http://jp.archive.ubuntu.com karmic-proposed/universe Packages                             
Hit http://security.ubuntu.com karmic-security Release.gpg                                     
Ign http://security.ubuntu.com karmic-security/main Translation-en_US                          
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US                    
Hit http://ppa.launchpad.net karmic Release.gpg                                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                                     
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Hit http://security.ubuntu.com karmic-security Release               
Hit http://packages.medibuntu.org karmic Release.gpg                 
Ign http://packages.medibuntu.org karmic/free Translation-en_US      
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US  
Hit http://ppa.launchpad.net karmic Release.gpg                      
Ign http://ppa.launchpad.net karmic/main Translation-en_US           
Hit http://ppa.launchpad.net karmic Release.gpg                      
Ign http://ppa.launchpad.net karmic/main Translation-en_US           
Hit http://ppa.launchpad.net karmic Release.gpg                      
Ign http://ppa.launchpad.net karmic/main Translation-en_US           
Hit http://ppa.launchpad.net karmic Release.gpg                      
Ign http://ppa.launchpad.net karmic/main Translation-en_US           
Hit http://ppa.launchpad.net karmic Release.gpg                      
Hit http://security.ubuntu.com karmic-security/main Packages         
Hit http://packages.medibuntu.org karmic Release                     
Ign http://ppa.launchpad.net karmic/main Translation-en_US         
Ign http://ppa.launchpad.net karmic Release.gpg                      
Ign http://ppa.launchpad.net karmic/main Translation-en_US           
Hit http://ppa.launchpad.net karmic Release.gpg                      
Ign http://ppa.launchpad.net karmic/main Translation-en_US           
Hit http://ppa.launchpad.net karmic Release                          
Hit http://ppa.launchpad.net karmic Release                          
Hit http://ppa.launchpad.net karmic Release                          
Hit http://ppa.launchpad.net karmic Release                          
Hit http://security.ubuntu.com karmic-security/restricted Packages                        
Hit http://security.ubuntu.com karmic-security/universe Packages     
Hit http://security.ubuntu.com karmic-security/multiverse Packages   
Hit http://packages.medibuntu.org karmic/free Packages               
Hit http://ppa.launchpad.net karmic Release    
Hit http://ppa.launchpad.net karmic Release    
Ign http://ppa.launchpad.net karmic Release    
Hit http://packages.medibuntu.org karmic/non-free Packages          
Hit http://ppa.launchpad.net karmic Release    
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Ign http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Ign http://ppa.launchpad.net karmic/main Packages
Err http://ppa.launchpad.net karmic/main Packages
  404  Not Found
W: Failed to fetch http://ppa.launchpad.net/ppa/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```Is the repo down or is it on my end: I never had any error prior errors message during my updates? And how do I troubleshoot* that?

* Changing server did not help

---

### Post by linuxman94 on 2010-05-28
Seems like that is not a valid PPA.  I looked at ppa.launchpad.net and it was not listed.  I would check your software sources in System -> Administration -> Software Sources and make sure there are no bad entries.

---

### Post by nomnex on 2010-05-28
here is my /etc/apt/source.list (current)

```
mt@fmv:/etc/apt$ cat sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://jp.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://jp.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://jp.archive.ubuntu.com/ubuntu/ karmic universe
deb http://jp.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://jp.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://jp.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://jp.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb http://ppa.launchpad.net/rvm/mplayer/ubuntu karmic main
deb http://ppa.launchpad.net/rvm/smplayer/ubuntu karmic main
deb http://ppa.launchpad.net/shutter/ppa/ubuntu karmic main
deb http://jp.archive.ubuntu.com/ubuntu/ karmic-proposed restricted main multiverse univers
```These are the 2 PPA lines generating an error 404 error message (bad URL), I had to uncomment, see: print-screen. 

How did they in my source file? Are they legitimate or related to some other PPA in anyway? Thanks for some input.

---

