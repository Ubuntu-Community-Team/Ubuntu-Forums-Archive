---
title: "Lucid Lynx default sources.list ?"
date: 2010-08-19
forum: General Help
---

### Post by silentrock on 2010-08-19
Some time ago,trying to install libgtk1.2 i modified sources.list and i just came back from vacations and found out that i cannot download any software from Ubuntu Software Center i get the following error message > Requires installation of untrusted packages

 The action would require the installation of packages from not authenticated sources. Details: playonlinuxI just visited the repos generator and edited sources.list with no changes on the ubuntu software center.

every time i run ```
sudo apt-get update
``` in the terminal 

i get this in response 

> silentrock@silentrock:~$ sudo apt-get update
E: Invalid operation updade
silentrock@silentrock:~$ sudo apt-get update
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]                        
Ign [http://ppa.launchpad.net/banshee-team/ppa/ubuntu/](http://ppa.launchpad.net/banshee-team/ppa/ubuntu/) lucid/main Translation-en_US
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]                        
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid Release.gpg                               
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Ign [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Ign [http://ppa.launchpad.net/blueman/ppa/ubuntu/](http://ppa.launchpad.net/blueman/ppa/ubuntu/) lucid/main Translation-en_US
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]              
Ign [http://ppa.launchpad.net/breathe-dev/ppa/ubuntu/](http://ppa.launchpad.net/breathe-dev/ppa/ubuntu/) lucid/main Translation-en_US
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]                        
Ign [http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu/](http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu/) lucid/main Translation-en_US
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]              
Ign [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/) lucid/main Translation-en_US
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]              
Ign [http://ppa.launchpad.net/kiwilinux-members/ppa/ubuntu/](http://ppa.launchpad.net/kiwilinux-members/ppa/ubuntu/) lucid/main Translation-en_US
Ign [http://deb.playonlinux.com/](http://deb.playonlinux.com/) lucid/main Translation-en_US                   
Ign [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-security Release.gpg                    
Ign [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release.gpg                         
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) lucid-getdeb/apps Translation-en_US      
Ign [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-proposed Release.gpg                    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [57.3kB]                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [57.3kB]                          
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [66.0kB]                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [57.3kB]                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [57.3kB]                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get:12 [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid Release [1,722B]                       
Ign [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid-proposed/restricted Translation-en_US
Ign [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid-proposed/universe Translation-en_US
Ign [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid-proposed/multiverse Translation-en_US
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-backports Release.gpg                   
Ign [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_US
Ign [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_US
Ign [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Get:13 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [57.3kB]                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid/main Packages                             
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid Release                                 
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-security Release                        
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-updates Release                         
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-proposed Release                        
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-backports Release                       
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid/main Packages                             
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid/universe Packages                       
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid/multiverse Packages                     
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid/main Sources                            
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid/multiverse Sources                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources                                
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid/main Packages                             
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release                   
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-security/restricted Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-security/universe Packages           
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-security/multiverse Packages         
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-security/main Sources                
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-security/restricted Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-security/universe Sources            
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-security/multiverse Sources          
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-updates/restricted Packages          
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-updates/universe Packages            
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-updates/multiverse Packages          
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-proposed/restricted Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-proposed/universe Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-proposed/multiverse Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-proposed/main Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-proposed/restricted Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-proposed/universe Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-proposed/multiverse Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-backports/restricted Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-backports/universe Packages
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/apps Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-backports/multiverse Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-backports/main Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-backports/restricted Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-backports/universe Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-backports/multiverse Sources
Fetched 1,849B in 3s (487B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6B15AB91951DC1E2
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 304E3B9E45FFBBBA
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7274A4DAE80D6BF5
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E1C8AC7385C2A3C7


---

### Post by oldos2er on 2010-08-20
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
```
where KEYID is number shown in error msg. Then run ```
sudo apt-get update
``` again.

---

