---
title: "Repository update &quot;really&quot; slow"
date: 2011-04-05
forum: General Help
---

### Post by Rushyang on 2011-04-05
Hey guys, I am facing a problem when I execute `sudo apt-get update`.. It's "really" slow. It takes over 20 minutes to complete the update... 

Here is output prompted on terminal while updating a repository..

```
Hit [http://extras.ubuntu.com]("http://extras.ubuntu.com/") maverick Release.gpg                                                                                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en                                                                              
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security Release.gpg                                                             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en                                             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_IN                                          
Get:1 [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release.gpg [316B]                                                                                     
Ign [http://ppa.launchpad.net/david4dev/qr/ubuntu/](http://ppa.launchpad.net/david4dev/qr/ubuntu/) maverick/main Translation-en                                                                   
Ign [http://ppa.launchpad.net/david4dev/qr/ubuntu/](http://ppa.launchpad.net/david4dev/qr/ubuntu/) maverick/main Translation-en_IN                                                               
Hit [http://archive.canonical.com]("http://archive.canonical.com/") maverick Release.gpg                                                                                           
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en                                                  
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_IN                                                      
Hit [http://extras.ubuntu.com]("http://extras.ubuntu.com/") maverick Release                                                                                                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en                                                              
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_IN                                     
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en                                        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_IN                                     
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en                                          
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_IN                                       
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release.gpg                                                                         
Ign [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/) maverick/main Translation-en                      
Ign [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/) maverick/main Translation-en_IN                   
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release.gpg                                                                         
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) maverick/main Translation-en                                              
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) maverick/main Translation-en_IN                                           
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release.gpg                                                                         
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security Release                                                                  
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_IN                                                                     
Hit [http://archive.canonical.com]("http://archive.canonical.com/") maverick Release                                                                                               
Ign [http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu/](http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu/) maverick/main Translation-en                                                             
Ign [http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu/](http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu/) maverick/main Translation-en_IN                                    
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release.gpg                                                                                               
Hit [http://extras.ubuntu.com]("http://extras.ubuntu.com/") maverick/main Sources                                                                                              
Ign [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/) maverick/main Translation-en                       
Ign [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/) maverick/main Translation-en_IN                    
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release.gpg                                                                         
Ign [http://ppa.launchpad.net/hotot-team/ppa/ubuntu/](http://ppa.launchpad.net/hotot-team/ppa/ubuntu/) maverick/main Translation-en                                          
Ign [http://ppa.launchpad.net/hotot-team/ppa/ubuntu/](http://ppa.launchpad.net/hotot-team/ppa/ubuntu/) maverick/main Translation-en_IN                                       
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/main Sources                                                             
Hit [http://archive.canonical.com]("http://archive.canonical.com/") maverick/partner Sources                                                                 
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release.gpg                                                                         
Ign [http://ppa.launchpad.net/nuovodna/nuovodna-stuff/ubuntu/](http://ppa.launchpad.net/nuovodna/nuovodna-stuff/ubuntu/) maverick/main Translation-en                                 
Hit [http://extras.ubuntu.com]("http://extras.ubuntu.com/") maverick/main amd64 Packages                                                                                       
Ign [http://ppa.launchpad.net/nuovodna/nuovodna-stuff/ubuntu/](http://ppa.launchpad.net/nuovodna/nuovodna-stuff/ubuntu/) maverick/main Translation-en_IN                                                    
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release.gpg                                                                         
Ign [http://ppa.launchpad.net/ricotz/testing/ubuntu/](http://ppa.launchpad.net/ricotz/testing/ubuntu/) maverick/main Translation-en                    
Ign [http://ppa.launchpad.net/ricotz/testing/ubuntu/](http://ppa.launchpad.net/ricotz/testing/ubuntu/) maverick/main Translation-en_IN                 
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release.gpg                                                   
Ign [http://ppa.launchpad.net/synapse-core/ppa/ubuntu/](http://ppa.launchpad.net/synapse-core/ppa/ubuntu/) maverick/main Translation-en                  
Ign [http://ppa.launchpad.net/synapse-core/ppa/ubuntu/](http://ppa.launchpad.net/synapse-core/ppa/ubuntu/) maverick/main Translation-en_IN               
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/restricted Sources                                                       
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/universe Sources                                                         
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/multiverse Sources                                                       
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/main amd64 Packages                                                      
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/restricted amd64 Packages                          
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/universe amd64 Packages                            
Hit [http://archive.canonical.com]("http://archive.canonical.com/") maverick/partner amd64 Packages                                                          
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/multiverse amd64 Packages                                                
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release.gpg                                                   
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en_IN
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release.gpg       
Ign [http://ppa.launchpad.net/webupd8team/themes/ubuntu/](http://ppa.launchpad.net/webupd8team/themes/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/webupd8team/themes/ubuntu/](http://ppa.launchpad.net/webupd8team/themes/ubuntu/) maverick/main Translation-en_IN
Get:2 [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release [9,745B]
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release                                                         
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release                                                         
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release                                                       
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release                                                       
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release                                                       
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release                                 
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release                                                       
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release                                                       
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release                                                       
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release                                                       
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release                                                       
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main Sources/DiffIndex                                        
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main amd64 Packages/DiffIndex           
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main Sources      
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main amd64 Packages
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main Sources                            
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main amd64 Packages                     
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main Sources                            
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main amd64 Packages                     
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main Sources                            
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main amd64 Packages                     
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main Sources                            
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main amd64 Packages                     
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main Sources      
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main amd64 Packages
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main Sources      
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main amd64 Packages
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main Sources                            
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main amd64 Packages                     
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main Sources      
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main amd64 Packages
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main Sources      
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main amd64 Packages
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main Sources      
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main amd64 Packages                     
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") maverick Release.gpg                                                                                            
[COLOR=DarkRed]Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_IN
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") maverick-updates Release.gpg
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") maverick Release
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") maverick-updates Release                     
99% [Connecting to in.archive.ubuntu.com (111.91.91.37)][/COLOR]

```Normal text from above quoted ran fast as usual.. but when I'm on 99%, that red text starts killing me taking more than 20 minutes or even more.. 

Here is my [sources.list]("https://github.com/rushyang/Nautilus-Scripts-for-Developers/raw/master/sources.list").

Thanks.

UPDATE:

It just got over now with some errors display after above coded output..
```

Err http://in.archive.ubuntu.com maverick/main Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com maverick/restricted Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com maverick/universe Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com maverick/multiverse Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com maverick/main amd64 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com maverick/restricted amd64 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com maverick/universe amd64 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com maverick/multiverse amd64 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com maverick-updates/main Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com maverick-updates/restricted Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com maverick-updates/universe Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com maverick-updates/multiverse Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com maverick-updates/main amd64 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com maverick-updates/restricted amd64 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com maverick-updates/universe amd64 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com maverick-updates/multiverse amd64 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Fetched 317B in 13min 57s (0B/s)
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A483D28094328634
W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-amd64/Packages.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-amd64/Packages.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-amd64/Packages.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-amd64/Packages.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-amd64/Packages.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-amd64/Packages.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-amd64/Packages.gz  Unable to connect to in.archive.ubuntu.com:http:

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

May be If someone could tell me which PPAs are unreachable, I could remove them from souces.list?

---

### Post by maverick555 on 2011-04-05
go to ubuntu software center -> edit at the left top -> software sources -> enter your password -> click on download from -> other -> select best server -> choose server once its finished.Then update.

---

### Post by Rushyang on 2011-04-06
> **maverick555 said:**
> go to ubuntu software center -> edit at the left top -> software sources -> enter your password -> click on download from -> other -> select best server -> choose server once its finished.Then update.


That worked like charm! Thanks.

---

