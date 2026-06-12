---
title: "Update Manager Error"
date: 2009-12-15
forum: General Help
---

### Post by superstalker on 2009-12-15
Got the following error:

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6D975C4791E7EE5EFailed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/karmic/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/karmic/main/binary-amd64/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.



Update Manager hasn't updated my system for over 7 days now, please help.

grtz

---

### Post by Polygon on 2009-12-15
go to system > administration > software sources

do you see two keys there for the Ubuntu automatic archive signing key and ubuntu cd image automatic signing key?

---

### Post by superstalker on 2009-12-15
Yes.

---

### Post by superstalker on 2009-12-16
... So what now?

---

### Post by philinux on 2009-12-16
> **superstalker said:**
> Got the following error:

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6D975C4791E7EE5EFailed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/karmic/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/karmic/main/binary-amd64/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.



Update Manager hasn't updated my system for over 7 days now, please help.

grtz

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6D975C4791E7EE5E


```

then

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by superstalker on 2009-12-16
[FONT=monospace]```
[/FONT]
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6D975C4791E7EE5E 
```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 6D975C4791E7EE5E
gpg: requesting key 91E7EE5E from hkp server keyserver.ubuntu.com
gpg: key 91E7EE5E: "Launchpad PPA for XBMC for Linux" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```

sudo apt-get update && sudo apt-get upgrade
```
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                                                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                                                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US                                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                                                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                                                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                                                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                                                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                                                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US                                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US                                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US                                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                                                               
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic Release.gpg                                                                  
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic/main Translation-en_US                                                  
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic/restricted Translation-en_US                                            
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic/universe Translation-en_US                                              
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic/multiverse Translation-en_US                                            
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic-updates Release.gpg                                                     
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic-updates/main Translation-en_US                                          
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic-updates/restricted Translation-en_US                                    
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic-updates/universe Translation-en_US                                      
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                                                     
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic Release                                                                 
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic-updates Release                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                             
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages       
  404  Not Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources                    
Get:1 [http://downloadue.info](http://downloadue.info) karmic Release.gpg
Ign [http://downloadue.info](http://downloadue.info) karmic/all Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                   
Ign [http://downloadue.info](http://downloadue.info) karmic Release                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                   
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic/main Packages               
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic/restricted Packages         
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic/main Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic/restricted Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic/universe Packages           
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic/universe Sources            
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic/multiverse Packages         
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic/multiverse Sources          
Ign [http://downloadue.info](http://downloadue.info) karmic/all Packages                      
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic-updates/main Packages       
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic-updates/universe Sources    
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic-updates/multiverse Packages 
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) karmic-updates/multiverse Sources  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                   
Ign [http://downloadue.info](http://downloadue.info) karmic/all Packages                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
Hit [http://downloadue.info](http://downloadue.info) karmic/all Packages
W: Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/karmic/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/karmic/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by philinux on 2009-12-16
[http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/karmic/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/karmic/main/binary-amd64/Packages.gz)

Looks like the ppa is off line for now then.

---

### Post by superstalker on 2009-12-16
Still nothing, except for the yellow triangle with a red exlamation mark that's annoying me bejeepers out of me.

Is it supposed to be offline for such a long period?

Edit: Could it's related to this topic: [http://ubuntuforums.org/showthread.php?t=1349619](http://ubuntuforums.org/showthread.php?t=1349619)

---

