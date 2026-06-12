---
title: "apt-upgrade error"
date: 2010-03-03
forum: General Help
---

### Post by CatchItBaby on 2010-03-03
```
root@anything:~# sudo apt-get update
Hit http://packages.medibuntu.org karmic Release.gpg
Ign http://packages.medibuntu.org karmic/free Translation-en_US                
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US            
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US      
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://us.archive.ubuntu.com karmic Release.gpg                            
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US             
Hit http://archive.ubuntu.com karmic Release.gpg                               
Ign http://archive.ubuntu.com karmic/main Translation-en_US                    
Hit http://archive.canonical.com karmic Release.gpg                            
Ign http://archive.canonical.com karmic/partner Translation-en_US              
Hit http://wine.budgetdedicated.com hardy Release.gpg                          
Ign http://wine.budgetdedicated.com hardy/main Translation-en_US               
Hit http://packages.medibuntu.org karmic Release                               
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com karmic-security Release                         
Hit http://ppa.launchpad.net karmic Release                                    
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US           
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg                    
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US   
Hit http://us.archive.ubuntu.com karmic Release                                
Ign http://archive.ubuntu.com karmic/restricted Translation-en_US              
Ign http://archive.ubuntu.com karmic/universe Translation-en_US                
Ign http://archive.ubuntu.com karmic/multiverse Translation-en_US              
Hit http://archive.ubuntu.com karmic-updates Release.gpg                       
Ign http://archive.ubuntu.com karmic-updates/main Translation-en_US            
Ign http://archive.ubuntu.com karmic-updates/restricted Translation-en_US      
Ign http://archive.ubuntu.com karmic-updates/universe Translation-en_US        
Ign http://archive.ubuntu.com karmic-updates/multiverse Translation-en_US      
Hit http://archive.ubuntu.com karmic-security Release.gpg                      
Hit http://archive.canonical.com karmic Release                                
Hit http://wine.budgetdedicated.com hardy Release                              
Ign http://archive.ubuntu.com karmic-security/main Translation-en_US           
Hit http://us.archive.ubuntu.com karmic-updates Release                        
Hit http://packages.medibuntu.org karmic/free Packages                         
Hit http://security.ubuntu.com karmic-security/universe Packages               
Hit http://ppa.launchpad.net karmic/main Packages                              
Ign http://archive.ubuntu.com karmic-security/restricted Translation-en_US     
Ign http://archive.ubuntu.com karmic-security/universe Translation-en_US       
Ign http://archive.ubuntu.com karmic-security/multiverse Translation-en_US     
Hit http://archive.ubuntu.com karmic Release                                   
Hit http://archive.ubuntu.com karmic-updates Release                           
Hit http://us.archive.ubuntu.com karmic/universe Packages                      
Hit http://us.archive.ubuntu.com karmic/universe Sources                       
Hit http://security.ubuntu.com karmic-security/universe Sources                
Hit http://security.ubuntu.com karmic-security/multiverse Packages             
Hit http://security.ubuntu.com karmic-security/multiverse Sources              
Hit http://packages.medibuntu.org karmic/non-free Packages                     
Hit http://archive.canonical.com karmic/partner Packages                       
Ign http://wine.budgetdedicated.com hardy/main Packages                        
Hit http://us.archive.ubuntu.com karmic/multiverse Packages                    
Hit http://us.archive.ubuntu.com karmic/multiverse Sources           
Hit http://archive.ubuntu.com karmic-security Release                
Hit http://wine.budgetdedicated.com hardy/main Sources                         
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages    
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources     
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages  
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources   
Hit http://archive.ubuntu.com karmic/main Packages                   
Hit http://archive.ubuntu.com karmic/restricted Packages
Hit http://archive.ubuntu.com karmic/main Sources
Hit http://archive.ubuntu.com karmic/restricted Sources
Hit http://archive.ubuntu.com karmic/universe Packages
Hit http://archive.ubuntu.com karmic/universe Sources
Hit http://archive.ubuntu.com karmic/multiverse Sources
Hit http://archive.ubuntu.com karmic/multiverse Packages
Hit http://archive.ubuntu.com karmic-updates/main Packages
Hit http://archive.ubuntu.com karmic-updates/restricted Packages
Ign http://wine.budgetdedicated.com hardy/main Packages
Hit http://archive.ubuntu.com karmic-updates/main Sources
Hit http://archive.ubuntu.com karmic-updates/restricted Sources
Hit http://wine.budgetdedicated.com hardy/main Packages
Hit http://archive.ubuntu.com karmic-updates/universe Packages
Hit http://archive.ubuntu.com karmic-updates/universe Sources
Hit http://archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://archive.ubuntu.com karmic-updates/multiverse Sources
Hit http://archive.ubuntu.com karmic-security/main Packages
Hit http://archive.ubuntu.com karmic-security/restricted Packages
Hit http://archive.ubuntu.com karmic-security/main Sources
Hit http://archive.ubuntu.com karmic-security/restricted Sources
Hit http://archive.ubuntu.com karmic-security/universe Packages
Hit http://archive.ubuntu.com karmic-security/universe Sources
Hit http://archive.ubuntu.com karmic-security/multiverse Packages
Hit http://archive.ubuntu.com karmic-security/multiverse Sources
Reading package lists... Done
root@anything:~# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  bind9-host dnsutils libbind9-50 libdns50 libisc50 libisccc50 libisccfg50
  liblwres50 linux-headers-generic sreadahead
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up libfox-1.6-dev (1.6.36-1) ...
update-alternatives: error: alternative path /usr/bin/fox-config-1.6 doesn't exist.
dpkg: error processing libfox-1.6-dev (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 libfox-1.6-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@anything:~# 


```

---

### Post by CatchItBaby on 2010-03-03
my sources.list file

```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic universe
deb http://archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb http://archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb http://archive.ubuntu.com/ubuntu/ karmic-security universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic-security universe
deb http://archive.ubuntu.com/ubuntu/ karmic-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic-security multiverse

## Wine, Ubuntu Hardy Heron (8.04):
deb http://wine.budgetdedicated.com/apt hardy main
deb-src http://wine.budgetdedicated.com/apt hardy main

deb http://archive.ubuntu.com/ubuntu karmic universe multiverse
deb-src http://archive.ubuntu.com/ubuntu karmic universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse

deb http://packages.medibuntu.org/ karmic free non-free
```

---

### Post by karthick87 on 2010-03-03
Try..
```

sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get update
```

---

### Post by CatchItBaby on 2010-03-03
Nothing happend see the output below


```
root@anything:~# sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
root@anything:~# sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up libfox-1.6-dev (1.6.36-1) ...
update-alternatives: error: alternative path /usr/bin/fox-config-1.6 doesn't exist.
dpkg: error processing libfox-1.6-dev (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 libfox-1.6-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@anything:~# sudo apt-get update
Hit http://packages.medibuntu.org karmic Release.gpg
Ign http://packages.medibuntu.org karmic/free Translation-en_US                
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US            
Hit http://wine.budgetdedicated.com hardy Release.gpg                          
Ign http://wine.budgetdedicated.com hardy/main Translation-en_US               
Hit http://us.archive.ubuntu.com karmic Release.gpg                            
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US             
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US      
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://archive.ubuntu.com karmic Release.gpg                               
Ign http://archive.ubuntu.com karmic/main Translation-en_US                    
Hit http://archive.canonical.com karmic Release.gpg                            
Ign http://archive.canonical.com karmic/partner Translation-en_US              
Hit http://packages.medibuntu.org karmic Release                               
Hit http://wine.budgetdedicated.com hardy Release                              
Ign http://archive.ubuntu.com karmic/restricted Translation-en_US              
Ign http://archive.ubuntu.com karmic/universe Translation-en_US                
Ign http://archive.ubuntu.com karmic/multiverse Translation-en_US              
Hit http://archive.ubuntu.com karmic-updates Release.gpg                       
Ign http://archive.ubuntu.com karmic-updates/main Translation-en_US            
Ign http://archive.ubuntu.com karmic-updates/restricted Translation-en_US      
Ign http://archive.ubuntu.com karmic-updates/universe Translation-en_US        
Ign http://archive.ubuntu.com karmic-updates/multiverse Translation-en_US      
Hit http://archive.ubuntu.com karmic-security Release.gpg                      
Hit http://archive.canonical.com karmic Release                                
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US           
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg                    
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US   
Hit http://us.archive.ubuntu.com karmic Release                                
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com karmic-security Release                         
Hit http://ppa.launchpad.net karmic Release                                    
Ign http://archive.ubuntu.com karmic-security/main Translation-en_US           
Ign http://archive.ubuntu.com karmic-security/restricted Translation-en_US     
Ign http://archive.ubuntu.com karmic-security/universe Translation-en_US       
Ign http://archive.ubuntu.com karmic-security/multiverse Translation-en_US     
Hit http://archive.ubuntu.com karmic Release                                   
Ign http://wine.budgetdedicated.com hardy/main Packages                        
Hit http://us.archive.ubuntu.com karmic-updates Release                        
Hit http://packages.medibuntu.org karmic/free Packages                         
Hit http://archive.canonical.com karmic/partner Packages                       
Hit http://archive.ubuntu.com karmic-updates Release                           
Hit http://archive.ubuntu.com karmic-security Release                          
Hit http://wine.budgetdedicated.com hardy/main Sources                         
Hit http://us.archive.ubuntu.com karmic/universe Packages                      
Hit http://us.archive.ubuntu.com karmic/universe Sources                       
Hit http://us.archive.ubuntu.com karmic/multiverse Packages                    
Hit http://us.archive.ubuntu.com karmic/multiverse Sources                     
Hit http://security.ubuntu.com karmic-security/universe Packages               
Hit http://packages.medibuntu.org karmic/non-free Packages                     
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://archive.ubuntu.com karmic/main Packages                             
Hit http://archive.ubuntu.com karmic/restricted Packages                       
Hit http://archive.ubuntu.com karmic/main Sources                              
Hit http://archive.ubuntu.com karmic/restricted Sources                        
Hit http://archive.ubuntu.com karmic/universe Packages                         
Hit http://archive.ubuntu.com karmic/universe Sources                          
Hit http://archive.ubuntu.com karmic/multiverse Sources                        
Ign http://wine.budgetdedicated.com hardy/main Packages                        
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages              
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources               
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages            
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources             
Hit http://security.ubuntu.com karmic-security/universe Sources                
Hit http://security.ubuntu.com karmic-security/multiverse Packages             
Hit http://security.ubuntu.com karmic-security/multiverse Sources              
Hit http://archive.ubuntu.com karmic/multiverse Packages                       
Hit http://archive.ubuntu.com karmic-updates/main Packages
Hit http://archive.ubuntu.com karmic-updates/restricted Packages
Hit http://archive.ubuntu.com karmic-updates/main Sources
Hit http://archive.ubuntu.com karmic-updates/restricted Sources
Hit http://archive.ubuntu.com karmic-updates/universe Packages
Hit http://archive.ubuntu.com karmic-updates/universe Sources
Hit http://archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://wine.budgetdedicated.com hardy/main Packages
Hit http://archive.ubuntu.com karmic-updates/multiverse Sources
Hit http://archive.ubuntu.com karmic-security/main Packages
Hit http://archive.ubuntu.com karmic-security/restricted Packages
Hit http://archive.ubuntu.com karmic-security/main Sources
Hit http://archive.ubuntu.com karmic-security/restricted Sources
Hit http://archive.ubuntu.com karmic-security/universe Packages
Hit http://archive.ubuntu.com karmic-security/universe Sources
Hit http://archive.ubuntu.com karmic-security/multiverse Packages
Hit http://archive.ubuntu.com karmic-security/multiverse Sources
Reading package lists... Done
root@anything:~# 


```

---

### Post by karthick87 on 2010-03-03
Go into /var/lib/dpkg/info and delete that name(libfox-1.6-dev) and you may also have to go into /var/cache/apt/archives and do the same thing...and then try again

---

### Post by CatchItBaby on 2010-03-03
In /var/lib/dpkg/info 

It show's thre file with same name

[IMG]http://i46.tinypic.com/v7tli1.jpg[/IMG]

and in /var/cache/apt/archives  There is no suck a file present

Afte removing and running these command's it don't show that error again

But it show

```
root@anything:~# sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
root@anything:~# sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up libfox-1.6-dev (1.6.36-1) ...
root@anything:~# sudo apt-get update
Hit http://packages.medibuntu.org karmic Release.gpg
Ign http://packages.medibuntu.org karmic/free Translation-en_US
Hit http://wine.budgetdedicated.com hardy Release.gpg                          
Ign http://wine.budgetdedicated.com hardy/main Translation-en_US               
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US      
Hit http://us.archive.ubuntu.com karmic Release.gpg                            
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US             
Hit http://archive.ubuntu.com karmic Release.gpg                               
Ign http://archive.ubuntu.com karmic/main Translation-en_US                    
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US            
Hit http://packages.medibuntu.org karmic Release                               
Ign http://archive.ubuntu.com karmic/restricted Translation-en_US              
Ign http://archive.ubuntu.com karmic/universe Translation-en_US                
Ign http://archive.ubuntu.com karmic/multiverse Translation-en_US              
Hit http://archive.ubuntu.com karmic-updates Release.gpg                       
Ign http://archive.ubuntu.com karmic-updates/main Translation-en_US            
Ign http://archive.ubuntu.com karmic-updates/restricted Translation-en_US      
Hit http://wine.budgetdedicated.com hardy Release                              
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US           
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg                    
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US   
Hit http://us.archive.ubuntu.com karmic Release                                
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com karmic-security Release                         
Hit http://ppa.launchpad.net karmic Release                                    
Ign http://archive.ubuntu.com karmic-updates/universe Translation-en_US        
Ign http://archive.ubuntu.com karmic-updates/multiverse Translation-en_US      
Hit http://archive.ubuntu.com karmic-security Release.gpg                      
Hit http://us.archive.ubuntu.com karmic-updates Release                        
Ign http://archive.ubuntu.com karmic-security/main Translation-en_US           
Ign http://archive.ubuntu.com karmic-security/restricted Translation-en_US     
Ign http://archive.ubuntu.com karmic-security/universe Translation-en_US       
Ign http://archive.ubuntu.com karmic-security/multiverse Translation-en_US     
Hit http://archive.ubuntu.com karmic Release                                   
Hit http://archive.ubuntu.com karmic-updates Release                           
Hit http://archive.ubuntu.com karmic-security Release                          
Hit http://archive.canonical.com karmic Release.gpg                            
Ign http://archive.canonical.com karmic/partner Translation-en_US
Hit http://archive.canonical.com karmic Release
Hit http://packages.medibuntu.org karmic/free Packages
Hit http://packages.medibuntu.org karmic/non-free Packages          
Ign http://wine.budgetdedicated.com hardy/main Packages             
Hit http://wine.budgetdedicated.com hardy/main Sources
Ign http://wine.budgetdedicated.com hardy/main Packages             
Hit http://us.archive.ubuntu.com karmic/universe Packages           
Hit http://wine.budgetdedicated.com hardy/main Packages
Hit http://us.archive.ubuntu.com karmic/universe Sources
Hit http://us.archive.ubuntu.com karmic/multiverse Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Sources
Hit http://security.ubuntu.com karmic-security/universe Packages
Hit http://security.ubuntu.com karmic-security/universe Sources
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://security.ubuntu.com karmic-security/multiverse Sources
Hit http://ppa.launchpad.net karmic/main Packages                   
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages   
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources    
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages 
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources  
Hit http://archive.ubuntu.com karmic/main Packages                  
Hit http://archive.ubuntu.com karmic/restricted Packages
Hit http://archive.ubuntu.com karmic/main Sources
Hit http://archive.ubuntu.com karmic/restricted Sources
Hit http://archive.ubuntu.com karmic/universe Packages
Hit http://archive.ubuntu.com karmic/universe Sources
Hit http://archive.ubuntu.com karmic/multiverse Sources
Hit http://archive.ubuntu.com karmic/multiverse Packages
Hit http://archive.ubuntu.com karmic-updates/main Packages
Hit http://archive.ubuntu.com karmic-updates/restricted Packages
Hit http://archive.ubuntu.com karmic-updates/main Sources
Hit http://archive.ubuntu.com karmic-updates/restricted Sources
Hit http://archive.ubuntu.com karmic-updates/universe Packages
Hit http://archive.ubuntu.com karmic-updates/universe Sources
Hit http://archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://archive.ubuntu.com karmic-updates/multiverse Sources
Hit http://archive.ubuntu.com karmic-security/main Packages
Hit http://archive.ubuntu.com karmic-security/restricted Packages
Hit http://archive.ubuntu.com karmic-security/main Sources
Hit http://archive.ubuntu.com karmic-security/restricted Sources
Hit http://archive.canonical.com karmic/partner Packages
Hit http://archive.ubuntu.com karmic-security/universe Packages
Hit http://archive.ubuntu.com karmic-security/universe Sources
Hit http://archive.ubuntu.com karmic-security/multiverse Packages
Hit http://archive.ubuntu.com karmic-security/multiverse Sources
Reading package lists... Done
root@anything:~# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
T[B][COLOR="Red"]he following packages have been kept back:
  bind9-host dnsutils libbind9-50 libdns50 libisc50 libisccc50 libisccfg50
  liblwres50 linux-headers-generic sreadahead[/COLOR][/B]
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
root@anything:~# 


```

How to solve this

---

### Post by CatchItBaby on 2010-03-03
And i tried to install tucan download manager i got this error in terminal

```
dpkg: warning: files list file for package `libfox-1.6-dev' missing, assuming package has no files currently installed.

```

---

