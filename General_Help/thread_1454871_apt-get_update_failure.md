---
title: "apt-get update failure"
date: 2010-04-15
forum: General Help
---

### Post by pratik_narain on 2010-04-15
Hello everyone. I've got this very strange problem in karmic. When I do "sudo apt-get update", the update process fails to download some repo files. I'm pasting the whole output of the command here
```

Ign http://in.archive.ubuntu.com karmic Release.gpg                            
Ign http://in.archive.ubuntu.com karmic/main Translation-en_US                 
Ign http://in.archive.ubuntu.com karmic/restricted Translation-en_US           
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://security.ubuntu.com karmic-security/main Translation-en_US          
Ign http://in.archive.ubuntu.com karmic/universe Translation-en_US             
Ign http://in.archive.ubuntu.com karmic/multiverse Translation-en_US           
Ign http://in.archive.ubuntu.com karmic-updates Release.gpg                    
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US    
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US      
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com karmic-security Release                         
Ign http://in.archive.ubuntu.com karmic-updates/main Translation-en_US         
Ign http://in.archive.ubuntu.com karmic-updates/restricted Translation-en_US   
Ign http://in.archive.ubuntu.com karmic-updates/universe Translation-en_US     
Ign http://in.archive.ubuntu.com karmic-updates/multiverse Translation-en_US   
Ign http://in.archive.ubuntu.com karmic Release                                
Hit http://security.ubuntu.com karmic-security/main Packages                   
Ign http://in.archive.ubuntu.com karmic-updates Release                        
Hit http://security.ubuntu.com karmic-security/restricted Packages             
Hit http://security.ubuntu.com karmic-security/main Sources                    
Ign http://in.archive.ubuntu.com karmic/main Packages                          
Hit http://deb.opera.com stable Release.gpg                                    
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Ign http://in.archive.ubuntu.com karmic/restricted Packages                    
Hit http://deb.opera.com stable Release                                        
Ign http://in.archive.ubuntu.com karmic/main Sources                           
Ign http://in.archive.ubuntu.com karmic/restricted Sources                     
Ign http://deb.opera.com stable/non-free Packages                              
Ign http://in.archive.ubuntu.com karmic/universe Packages                      
Ign http://deb.opera.com stable/non-free Packages                              
Ign http://in.archive.ubuntu.com karmic/universe Sources                       
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://in.archive.ubuntu.com karmic/multiverse Packages                    
Ign http://in.archive.ubuntu.com karmic/multiverse Sources                     
Ign http://in.archive.ubuntu.com karmic-updates/main Packages                  
Hit http://security.ubuntu.com karmic-security/restricted Sources              
Hit http://security.ubuntu.com karmic-security/universe Packages               
Hit http://security.ubuntu.com karmic-security/universe Sources                
Hit http://security.ubuntu.com karmic-security/multiverse Packages             
Ign http://in.archive.ubuntu.com karmic-updates/restricted Packages            
Hit http://security.ubuntu.com karmic-security/multiverse Sources              
Hit http://deb.opera.com stable/non-free Packages                              
Ign http://in.archive.ubuntu.com karmic-updates/main Sources         
Ign http://in.archive.ubuntu.com karmic-updates/restricted Sources
Ign http://in.archive.ubuntu.com karmic-updates/universe Packages
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Ign http://in.archive.ubuntu.com karmic-updates/universe Sources
Get:1 http://ppa.launchpad.net karmic Release.gpg [307B]
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Ign http://in.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://ppa.launchpad.net karmic Release                                   
Hit http://ppa.launchpad.net karmic Release                                   
Hit http://ppa.launchpad.net karmic Release                                   
Hit http://ppa.launchpad.net karmic Release                                   
Get:2 http://ppa.launchpad.net karmic Release [66.0kB]                         
Ign http://ppa.launchpad.net karmic Release                                    
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://ppa.launchpad.net karmic/main Packages                              
Ign http://in.archive.ubuntu.com karmic-updates/multiverse Sources             
Ign http://in.archive.ubuntu.com karmic/main Packages                          
Ign http://in.archive.ubuntu.com karmic/restricted Packages
Ign http://in.archive.ubuntu.com karmic/main Sources
Ign http://in.archive.ubuntu.com karmic/restricted Sources
Ign http://in.archive.ubuntu.com karmic/universe Packages
Ign http://in.archive.ubuntu.com karmic/universe Sources
Ign http://in.archive.ubuntu.com karmic/multiverse Packages
Ign http://in.archive.ubuntu.com karmic/multiverse Sources
Ign http://in.archive.ubuntu.com karmic-updates/main Packages
Ign http://in.archive.ubuntu.com karmic-updates/restricted Packages
Ign http://in.archive.ubuntu.com karmic-updates/main Sources
Ign http://in.archive.ubuntu.com karmic-updates/restricted Sources
Ign http://in.archive.ubuntu.com karmic-updates/universe Packages
Ign http://in.archive.ubuntu.com karmic-updates/universe Sources
Ign http://in.archive.ubuntu.com karmic-updates/multiverse Packages
Ign http://in.archive.ubuntu.com karmic-updates/multiverse Sources
Err http://in.archive.ubuntu.com karmic/main Packages   
  404  Not Found
Err http://in.archive.ubuntu.com karmic/restricted Packages
  404  Not Found
Err http://in.archive.ubuntu.com karmic/main Sources    
  404  Not Found
Err http://in.archive.ubuntu.com karmic/restricted Sources
  404  Not Found
Err http://in.archive.ubuntu.com karmic/universe Packages
  404  Not Found
Err http://in.archive.ubuntu.com karmic/universe Sources
  404  Not Found
Err http://in.archive.ubuntu.com karmic/multiverse Packages
  404  Not Found
Err http://in.archive.ubuntu.com karmic/multiverse Sources
  404  Not Found
Err http://in.archive.ubuntu.com karmic-updates/main Packages
  404  Not Found
Err http://in.archive.ubuntu.com karmic-updates/restricted Packages
  404  Not Found
Err http://in.archive.ubuntu.com karmic-updates/main Sources
  404  Not Found
Err http://in.archive.ubuntu.com karmic-updates/restricted Sources
  404  Not Found
Err http://in.archive.ubuntu.com karmic-updates/universe Packages
  404  Not Found
Err http://in.archive.ubuntu.com karmic-updates/universe Sources
  404  Not Found
Err http://in.archive.ubuntu.com karmic-updates/multiverse Packages
  404  Not Found
Err http://in.archive.ubuntu.com karmic-updates/multiverse Sources
  404  Not Found
Fetched 308B in 2min 39s (2B/s)
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 64A9CDD77362E5D0
W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


```
kindly look into it and tell me the solution if possible so that I can update my system. Due to this problem i'm not able to install libqt4-opengl which required for virtualbox.

Also, an off topic question, I can't autocomplete words in shell specifically after sudo apt-get and in some cases after sudo also. The autocompletion is working in all the other cases.
Thank you.

---

### Post by zvacet on 2010-04-15
system>admin>software sources and change server to main and see if that helps.

---

