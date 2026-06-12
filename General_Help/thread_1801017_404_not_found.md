---
title: "404 not found"
date: 2011-07-09
forum: General Help
---

### Post by rudedcam on 2011-07-09
hi! anytime I try to install an application or make an update, i get a 404 not found error message. 
here's an example:
```
***@***:~$ sudo apt-get install flpsed
[sudo] password for rudecam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libclucene0ldbl ttf-wqy-zenhei ttf-kannada-fonts latex-xft-fonts liblualib50 libaccess-bridge-java librasqal1 ttf-telugu-fonts imagemagick-doc rhino ttf-oriya-fonts
  liblua50 ttf-bengali-fonts libwv2-1c2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libfltk1.1
The following NEW packages will be installed:
  flpsed libfltk1.1
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 493kB of archives.
After this operation, 1274kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libfltk1.1 flpsed
Install these packages without verification [y/N]? y
[COLOR="Red"]Err http://ca.archive.ubuntu.com jaunty/main libfltk1.1 1.1.9-6
  404 Not Found [IP: 91.189.88.45 80]
Err http://ca.archive.ubuntu.com jaunty/universe flpsed 0.5.1-2
  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/f/fltk1.1/libfltk1.1_1.1.9-6_i386.deb 404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/universe/f/flpsed/flpsed_0.5.1-2_i386.deb 404 Not Found [IP: 91.189.88.45 80]
[/COLOR]E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.
***@***:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
***@***:~$ sudo apt-get update
Ign http://ca.archive.ubuntu.com jaunty Release.gpg
Ign http://ca.archive.ubuntu.com jaunty/main Translation-en_CA                                                                                                         
Ign http://ca.archive.ubuntu.com jaunty/restricted Translation-en_CA                                                                                                   
Ign http://security.ubuntu.com jaunty-security Release.gpg                                                                                                             
Ign http://ca.archive.ubuntu.com jaunty/universe Translation-en_CA                                                                                     
Ign http://ca.archive.ubuntu.com jaunty/multiverse Translation-en_CA                                                              
Ign http://ca.archive.ubuntu.com jaunty-updates Release.gpg                                                                       
Ign http://ca.archive.ubuntu.com jaunty-updates/main Translation-en_CA                                                            
Ign http://ca.archive.ubuntu.com jaunty-updates/restricted Translation-en_CA                                                      
Ign http://ca.archive.ubuntu.com jaunty-updates/universe Translation-en_CA                                                        
Ign http://ca.archive.ubuntu.com jaunty-updates/multiverse Translation-en_CA                                                      
Ign http://ca.archive.ubuntu.com jaunty-backports Release.gpg                                                                     
Ign http://ca.archive.ubuntu.com jaunty-backports/main Translation-en_CA                                                                                
Ign http://archive.ubuntu.com jaunty Release.gpg                                                                                                        
Ign http://security.ubuntu.com jaunty-security/main Translation-en_CA                                                                                   
Hit http://archive.canonical.com jaunty Release.gpg                                                                               
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_CA                                                       
Ign http://archive.canonical.com jaunty/partner Translation-en_CA                                                                 
Ign http://ca.archive.ubuntu.com jaunty-backports/restricted Translation-en_CA                                                    
Ign http://ca.archive.ubuntu.com jaunty-backports/universe Translation-en_CA                                                      
Ign http://ca.archive.ubuntu.com jaunty-backports/multiverse Translation-en_CA                                                    
Ign http://ca.archive.ubuntu.com jaunty Release                                                                                   
Ign http://ca.archive.ubuntu.com jaunty-updates Release                                                                           
Ign http://archive.ubuntu.com jaunty Release                                                                                                            
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_CA                                                                               
Hit http://archive.canonical.com jaunty Release                                                                  
Ign http://ca.archive.ubuntu.com jaunty-backports Release                                                        
Ign http://ca.archive.ubuntu.com jaunty/main Packages                                                                                 
Ign http://ca.archive.ubuntu.com jaunty/restricted Packages                                                                           
Ign http://ca.archive.ubuntu.com jaunty/restricted Sources                                                                            
Ign http://ca.archive.ubuntu.com jaunty/main Sources                                                                                  
Ign http://ca.archive.ubuntu.com jaunty/multiverse Sources                                                                            
Ign http://ca.archive.ubuntu.com jaunty/universe Sources                                                                              
Ign http://archive.ubuntu.com jaunty/main Sources                                                                                     
Hit http://packages.medibuntu.org jaunty Release.gpg                                                                                  
Ign http://ca.archive.ubuntu.com jaunty/universe Packages                                                        
Ign http://ca.archive.ubuntu.com jaunty/multiverse Packages                                                                            
Ign http://ca.archive.ubuntu.com jaunty-updates/main Packages                                                                          
Ign http://ca.archive.ubuntu.com jaunty-updates/restricted Packages                                                                    
Ign http://ca.archive.ubuntu.com jaunty-updates/restricted Sources                                               
Ign http://ca.archive.ubuntu.com jaunty-updates/main Sources                                                     
Ign http://archive.ubuntu.com jaunty/restricted Sources                                                          
Hit http://archive.getdeb.net jaunty-getdeb Release.gpg                                                          
Ign http://ca.archive.ubuntu.com jaunty-updates/multiverse Sources                                               
Ign http://ca.archive.ubuntu.com jaunty-updates/universe Sources                                                 
Ign http://archive.getdeb.net jaunty-getdeb/apps Translation-en_CA                                               
Hit http://archive.canonical.com jaunty/partner Packages                                                         
Ign http://ca.archive.ubuntu.com jaunty-updates/universe Packages                                                
Ign http://ca.archive.ubuntu.com jaunty-updates/multiverse Packages                                              
Ign http://ca.archive.ubuntu.com jaunty-backports/main Packages                                                  
Ign http://archive.ubuntu.com jaunty/main Sources                                                                                      
Hit http://archive.canonical.com jaunty/partner Sources                                                                                
Ign http://ca.archive.ubuntu.com jaunty-backports/restricted Packages                                            
Ign http://ca.archive.ubuntu.com jaunty-backports/universe Packages                                              
Ign http://ca.archive.ubuntu.com jaunty-backports/multiverse Packages                                            
Ign http://ca.archive.ubuntu.com jaunty-backports/main Sources                                                   
Ign http://ca.archive.ubuntu.com jaunty-backports/restricted Sources                                             
Ign http://ca.archive.ubuntu.com jaunty-backports/universe Sources                         
Ign http://packages.medibuntu.org jaunty/free Translation-en_CA                                                  
Ign http://archive.ubuntu.com jaunty/restricted Sources                                                                                           
Ign http://ca.archive.ubuntu.com jaunty-backports/multiverse Sources                                                                              
Ign http://ca.archive.ubuntu.com jaunty/main Packages                                                            
Ign http://ca.archive.ubuntu.com jaunty/restricted Packages                                                      
Ign http://ca.archive.ubuntu.com jaunty/restricted Sources                                                       
Ign http://ca.archive.ubuntu.com jaunty/main Sources                                                             
Err http://archive.ubuntu.com jaunty/main Sources                                                                
  404 Not Found [IP: 91.189.88.30 80]
Ign http://ca.archive.ubuntu.com jaunty/multiverse Sources                                                       
Ign http://ca.archive.ubuntu.com jaunty/universe Sources                                   
Ign http://ca.archive.ubuntu.com jaunty/universe Packages                                  
Ign http://ca.archive.ubuntu.com jaunty/multiverse Packages                                
Ign http://ca.archive.ubuntu.com jaunty-updates/main Packages                              
Ign http://ca.archive.ubuntu.com jaunty-updates/restricted Packages                        
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_CA                                              
Hit http://archive.getdeb.net jaunty-getdeb Release                                                              
Err http://archive.ubuntu.com jaunty/restricted Sources                                                        
  404 Not Found [IP: 91.189.88.30 80]
Ign http://ca.archive.ubuntu.com jaunty-updates/restricted Sources                                             
Ign http://ca.archive.ubuntu.com jaunty-updates/main Sources                             
Ign http://ca.archive.ubuntu.com jaunty-updates/multiverse Sources                       
Ign http://ca.archive.ubuntu.com jaunty-updates/universe Sources                         
Ign http://ca.archive.ubuntu.com jaunty-updates/universe Packages                        
Ign http://ca.archive.ubuntu.com jaunty-updates/multiverse Packages                      
Ign http://ca.archive.ubuntu.com jaunty-backports/main Packages      
Ign http://ca.archive.ubuntu.com jaunty-backports/restricted Packages
Ign http://ca.archive.ubuntu.com jaunty-backports/universe Packages  
Ign http://ca.archive.ubuntu.com jaunty-backports/multiverse Packages
Ign http://ca.archive.ubuntu.com jaunty-backports/main Sources       
Hit http://packages.medibuntu.org jaunty Release                                           
Ign http://ca.archive.ubuntu.com jaunty-backports/restricted Sources                       
Ign http://ca.archive.ubuntu.com jaunty-backports/universe Sources                        
Ign http://ca.archive.ubuntu.com jaunty-backports/multiverse Sources                      
Err http://ca.archive.ubuntu.com jaunty/main Packages                                     
  404 Not Found [IP: 91.189.88.40 80]
Err http://ca.archive.ubuntu.com jaunty/restricted Packages                               
  404 Not Found [IP: 91.189.88.40 80]
Err http://ca.archive.ubuntu.com jaunty/restricted Sources                                
  404 Not Found [IP: 91.189.88.40 80]
Err http://ca.archive.ubuntu.com jaunty/main Sources                                       
  404 Not Found [IP: 91.189.88.40 80]
Err http://ca.archive.ubuntu.com jaunty/multiverse Sources                                 
  404 Not Found [IP: 91.189.88.40 80]
Err http://ca.archive.ubuntu.com jaunty/universe Sources                                   
  404 Not Found [IP: 91.189.88.40 80]
Err http://ca.archive.ubuntu.com jaunty/universe Packages                                  
  404 Not Found [IP: 91.189.88.40 80]
Err http://ca.archive.ubuntu.com jaunty/multiverse Packages          
  404 Not Found [IP: 91.189.88.40 80]
Err http://ca.archive.ubuntu.com jaunty-updates/main Packages                              
  404 Not Found [IP: 91.189.88.40 80]
Err http://ca.archive.ubuntu.com jaunty-updates/restricted Packages                        
  404 Not Found [IP: 91.189.88.40 80]
Err http://ca.archive.ubuntu.com jaunty-updates/restricted Sources                         
  404 Not Found [IP: 91.189.88.40 80]
Err http://ca.archive.ubuntu.com jaunty-updates/main Sources         
  404 Not Found [IP: 91.189.88.40 80]
Err http://ca.archive.ubuntu.com jaunty-updates/multiverse Sources   
  404 Not Found [IP: 91.189.88.40 80]
Hit http://archive.getdeb.net jaunty-getdeb/apps Packages                                  
Hit http://packages.medibuntu.org jaunty/free Packages                                     
Err http://ca.archive.ubuntu.com jaunty-updates/universe Sources     
  404 Not Found [IP: 91.189.88.40 80]
Err http://ca.archive.ubuntu.com jaunty-updates/universe Packages
  404 Not Found [IP: 91.189.88.40 80]
Err http://ca.archive.ubuntu.com jaunty-updates/multiverse Packages
  404 Not Found [IP: 91.189.88.40 80]
Err http://ca.archive.ubuntu.com jaunty-backports/main Packages
  404 Not Found [IP: 91.189.88.40 80]
Err http://ca.archive.ubuntu.com jaunty-backports/restricted Packages
  404 Not Found [IP: 91.189.88.40 80]
Err http://ca.archive.ubuntu.com jaunty-backports/universe Packages
  404 Not Found [IP: 91.189.88.40 80]
Err http://ca.archive.ubuntu.com jaunty-backports/multiverse Packages
  404 Not Found [IP: 91.189.88.40 80]
Err http://ca.archive.ubuntu.com jaunty-backports/main Sources       
  404 Not Found [IP: 91.189.88.40 80]
Err http://ca.archive.ubuntu.com jaunty-backports/restricted Sources 
  404 Not Found [IP: 91.189.88.40 80]
Err http://ca.archive.ubuntu.com jaunty-backports/universe Sources   
  404 Not Found [IP: 91.189.88.40 80]
Err http://ca.archive.ubuntu.com jaunty-backports/multiverse Sources 
  404 Not Found [IP: 91.189.88.40 80]
Hit http://packages.medibuntu.org jaunty/non-free Packages
Hit http://packages.medibuntu.org jaunty/free Sources                           
Hit http://packages.medibuntu.org jaunty/non-free Sources                       
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_CA
Ign http://security.ubuntu.com jaunty-security Release
Ign http://security.ubuntu.com jaunty-security/main Packages
Ign http://security.ubuntu.com jaunty-security/restricted Packages
Ign http://security.ubuntu.com jaunty-security/restricted Sources
Ign http://security.ubuntu.com jaunty-security/main Sources
Ign http://security.ubuntu.com jaunty-security/multiverse Sources
Ign http://security.ubuntu.com jaunty-security/universe Sources
Ign http://security.ubuntu.com jaunty-security/universe Packages
Ign http://security.ubuntu.com jaunty-security/multiverse Packages
Ign http://security.ubuntu.com jaunty-security/main Packages
Ign http://security.ubuntu.com jaunty-security/restricted Packages
Ign http://security.ubuntu.com jaunty-security/restricted Sources
Ign http://security.ubuntu.com jaunty-security/main Sources
Ign http://security.ubuntu.com jaunty-security/multiverse Sources
Ign http://security.ubuntu.com jaunty-security/universe Sources
Ign http://security.ubuntu.com jaunty-security/universe Packages
Ign http://security.ubuntu.com jaunty-security/multiverse Packages
Err http://security.ubuntu.com jaunty-security/main Packages
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com jaunty-security/restricted Packages
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com jaunty-security/restricted Sources
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com jaunty-security/main Sources
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com jaunty-security/multiverse Sources
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com jaunty-security/universe Sources
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com jaunty-security/universe Packages
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com jaunty-security/multiverse Packages
  404 Not Found [IP: 91.189.92.167 80]
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/source/Sources  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/source/Sources  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/source/Sources  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/source/Sources  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages  404 Not Found [IP: 91.189.92.167 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
***@***:~$ 


```
my guts tells me the problem is on my end and easily fixable. could anyone explain?
i'm using 9.04

thx

---

### Post by Habitual on 2011-07-09
> **rudedcam said:**
> my guts tells me the problem is on my end...

That's just gas. Eat something ;) It is a problem at the repo.(Unable to fetch some archives).
```
sudo apt-get update
``` and/or Try tomorrow.

---

### Post by rudedcam on 2011-07-09
ok, i'll wait,
```
***@***:~$  sudo apt-get update
[sudo] password for rudecam: 
Ign http://security.ubuntu.com jaunty-security Release.gpg
Hit http://archive.canonical.com jaunty Release.gpg                                                                                                    
Ign http://archive.ubuntu.com jaunty Release.gpg                                                                                                        
Ign http://ca.archive.ubuntu.com jaunty Release.gpg                                                                                                     
Ign http://ca.archive.ubuntu.com jaunty/main Translation-en_CA                                                                                                         
Ign http://ca.archive.ubuntu.com jaunty/restricted Translation-en_CA                                                                                                   
Ign http://security.ubuntu.com jaunty-security/main Translation-en_CA                                                                  
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_CA                                                            
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_CA                                                              
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_CA                                                            
Ign http://archive.canonical.com jaunty/partner Translation-en_CA                                                                      
Ign http://archive.ubuntu.com jaunty Release                                                                                           
Ign http://ca.archive.ubuntu.com jaunty/universe Translation-en_CA                                               
Ign http://ca.archive.ubuntu.com jaunty/multiverse Translation-en_CA                                             
Ign http://ca.archive.ubuntu.com jaunty-updates Release.gpg                                                      
Ign http://ca.archive.ubuntu.com jaunty-updates/main Translation-en_CA                                           
Ign http://ca.archive.ubuntu.com jaunty-updates/restricted Translation-en_CA                                     
Ign http://ca.archive.ubuntu.com jaunty-updates/universe Translation-en_CA                                                             
Ign http://ca.archive.ubuntu.com jaunty-updates/multiverse Translation-en_CA                                                           
Ign http://ca.archive.ubuntu.com jaunty-backports Release.gpg                                                                          
Ign http://security.ubuntu.com jaunty-security Release                                                                                 
Hit http://archive.canonical.com jaunty Release                                                                                        
Ign http://archive.ubuntu.com jaunty/main Sources                                                                                     
Hit http://packages.medibuntu.org jaunty Release.gpg                                                                                  
Ign http://ca.archive.ubuntu.com jaunty-backports/main Translation-en_CA                                                                                               
Ign http://ca.archive.ubuntu.com jaunty-backports/restricted Translation-en_CA                                                                                         
Ign http://ca.archive.ubuntu.com jaunty-backports/universe Translation-en_CA                                                          
Ign http://security.ubuntu.com jaunty-security/main Packages                                                                          
Hit http://archive.getdeb.net jaunty-getdeb Release.gpg                                                          
Ign http://archive.ubuntu.com jaunty/restricted Sources                                                                                
Ign http://archive.getdeb.net jaunty-getdeb/apps Translation-en_CA                                                                     
Ign http://ca.archive.ubuntu.com jaunty-backports/multiverse Translation-en_CA                                   
Ign http://ca.archive.ubuntu.com jaunty Release                                                                  
Ign http://ca.archive.ubuntu.com jaunty-updates Release                                                          
Hit http://archive.canonical.com jaunty/partner Packages                                                         
Ign http://security.ubuntu.com jaunty-security/restricted Packages                                                                             
Ign http://archive.ubuntu.com jaunty/main Sources                                                                                              
Ign http://packages.medibuntu.org jaunty/free Translation-en_CA                                                                        
Hit http://archive.canonical.com jaunty/partner Sources                                                                                                                
Ign http://security.ubuntu.com jaunty-security/restricted Sources                                                                                                      
Ign http://security.ubuntu.com jaunty-security/main Sources                                                      
Ign http://ca.archive.ubuntu.com jaunty-backports Release                                                        
Ign http://security.ubuntu.com jaunty-security/multiverse Sources                                                
Ign http://security.ubuntu.com jaunty-security/universe Sources                                                  
Ign http://security.ubuntu.com jaunty-security/universe Packages                                                 
Ign http://security.ubuntu.com jaunty-security/multiverse Packages                                               
Ign http://ca.archive.ubuntu.com jaunty/main Packages                                                            
Ign http://ca.archive.ubuntu.com jaunty/restricted Packages                                                      
Ign http://ca.archive.ubuntu.com jaunty/restricted Sources                                                       
Ign http://ca.archive.ubuntu.com jaunty/main Sources                                                             
Ign http://ca.archive.ubuntu.com jaunty/multiverse Sources                                                       
Ign http://ca.archive.ubuntu.com jaunty/universe Sources                                   
Ign http://archive.ubuntu.com jaunty/restricted Sources                                                          
Ign http://security.ubuntu.com jaunty-security/main Packages                                                     
Ign http://ca.archive.ubuntu.com jaunty/universe Packages                                                        
Ign http://ca.archive.ubuntu.com jaunty/multiverse Packages                                                                       
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_CA                                                               
Err http://archive.ubuntu.com jaunty/main Sources                                                                                                 
  404 Not Found [IP: 91.189.88.46 80]
Ign http://security.ubuntu.com jaunty-security/restricted Packages                                                                                
Ign http://security.ubuntu.com jaunty-security/restricted Sources                                                
Ign http://security.ubuntu.com jaunty-security/main Sources                                                      
Ign http://security.ubuntu.com jaunty-security/multiverse Sources                                                
Ign http://security.ubuntu.com jaunty-security/universe Sources                                                  
Ign http://security.ubuntu.com jaunty-security/universe Packages                           
Ign http://ca.archive.ubuntu.com jaunty-updates/main Packages                                                    
Ign http://ca.archive.ubuntu.com jaunty-updates/restricted Packages                                              
Ign http://ca.archive.ubuntu.com jaunty-updates/restricted Sources                                               
Ign http://ca.archive.ubuntu.com jaunty-updates/main Sources                                                     
Ign http://ca.archive.ubuntu.com jaunty-updates/multiverse Sources                                               
Ign http://ca.archive.ubuntu.com jaunty-updates/universe Sources                           
Ign http://ca.archive.ubuntu.com jaunty-updates/universe Packages                                                
Ign http://ca.archive.ubuntu.com jaunty-updates/multiverse Packages                                              
Ign http://ca.archive.ubuntu.com jaunty-backports/main Packages                                                  
Err http://archive.ubuntu.com jaunty/restricted Sources                                                          
  404 Not Found [IP: 91.189.88.46 80]
Hit http://archive.getdeb.net jaunty-getdeb Release                                                              
Ign http://security.ubuntu.com jaunty-security/multiverse Packages                         
Ign http://ca.archive.ubuntu.com jaunty-backports/restricted Packages                    
Ign http://ca.archive.ubuntu.com jaunty-backports/universe Packages                      
Ign http://ca.archive.ubuntu.com jaunty-backports/multiverse Packages                    
Ign http://ca.archive.ubuntu.com jaunty-backports/main Sources                           
Ign http://ca.archive.ubuntu.com jaunty-backports/restricted Sources                     
Ign http://ca.archive.ubuntu.com jaunty-backports/universe Sources
Hit http://packages.medibuntu.org jaunty Release                                                        
Err http://security.ubuntu.com jaunty-security/main Packages                                            
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com jaunty-security/restricted Packages                        
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com jaunty-security/restricted Sources                         
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com jaunty-security/main Sources                               
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com jaunty-security/multiverse Sources                         
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com jaunty-security/universe Sources                           
  404 Not Found [IP: 91.189.92.167 80]
Ign http://ca.archive.ubuntu.com jaunty-backports/multiverse Sources                      
Ign http://ca.archive.ubuntu.com jaunty/main Packages                
Ign http://ca.archive.ubuntu.com jaunty/restricted Packages          
Ign http://ca.archive.ubuntu.com jaunty/restricted Sources           
Ign http://ca.archive.ubuntu.com jaunty/main Sources                 
Err http://security.ubuntu.com jaunty-security/universe Packages                           
  404 Not Found [IP: 91.189.92.167 80]
Ign http://ca.archive.ubuntu.com jaunty/multiverse Sources                                 
Ign http://ca.archive.ubuntu.com jaunty/universe Sources                                   
Ign http://ca.archive.ubuntu.com jaunty/universe Packages                                  
Ign http://ca.archive.ubuntu.com jaunty/multiverse Packages                                
Ign http://ca.archive.ubuntu.com jaunty-updates/main Packages                              
Ign http://ca.archive.ubuntu.com jaunty-updates/restricted Packages  
Err http://security.ubuntu.com jaunty-security/multiverse Packages                         
  404 Not Found [IP: 91.189.92.167 80]
Hit http://packages.medibuntu.org jaunty/free Packages                                     
Ign http://ca.archive.ubuntu.com jaunty-updates/restricted Sources   
Ign http://ca.archive.ubuntu.com jaunty-updates/main Sources
Ign http://ca.archive.ubuntu.com jaunty-updates/multiverse Sources
Ign http://ca.archive.ubuntu.com jaunty-updates/universe Sources
Ign http://ca.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://archive.getdeb.net jaunty-getdeb/apps Packages            
Ign http://ca.archive.ubuntu.com jaunty-updates/multiverse Packages  
Ign http://ca.archive.ubuntu.com jaunty-backports/main Packages
Ign http://ca.archive.ubuntu.com jaunty-backports/restricted Packages
Ign http://ca.archive.ubuntu.com jaunty-backports/universe Packages
Ign http://ca.archive.ubuntu.com jaunty-backports/multiverse Packages
Ign http://ca.archive.ubuntu.com jaunty-backports/main Sources
Hit http://packages.medibuntu.org jaunty/non-free Packages
Ign http://ca.archive.ubuntu.com jaunty-backports/restricted Sources            
Ign http://ca.archive.ubuntu.com jaunty-backports/universe Sources              
Ign http://ca.archive.ubuntu.com jaunty-backports/multiverse Sources            
Err http://ca.archive.ubuntu.com jaunty/main Packages                           
  404 Not Found [IP: 91.189.88.30 80]
Err http://ca.archive.ubuntu.com jaunty/restricted Packages
  404 Not Found [IP: 91.189.88.30 80]
Err http://ca.archive.ubuntu.com jaunty/restricted Sources
  404 Not Found [IP: 91.189.88.30 80]
Err http://ca.archive.ubuntu.com jaunty/main Sources
  404 Not Found [IP: 91.189.88.30 80]
Err http://ca.archive.ubuntu.com jaunty/multiverse Sources
  404 Not Found [IP: 91.189.88.30 80]
Err http://ca.archive.ubuntu.com jaunty/universe Sources
  404 Not Found [IP: 91.189.88.30 80]
Err http://ca.archive.ubuntu.com jaunty/universe Packages
  404 Not Found [IP: 91.189.88.30 80]
Err http://ca.archive.ubuntu.com jaunty/multiverse Packages
  404 Not Found [IP: 91.189.88.30 80]
Hit http://packages.medibuntu.org jaunty/free Sources
Err http://ca.archive.ubuntu.com jaunty-updates/main Packages                   
  404 Not Found [IP: 91.189.88.30 80]
Err http://ca.archive.ubuntu.com jaunty-updates/restricted Packages             
  404 Not Found [IP: 91.189.88.30 80]
Err http://ca.archive.ubuntu.com jaunty-updates/restricted Sources
  404 Not Found [IP: 91.189.88.30 80]
Err http://ca.archive.ubuntu.com jaunty-updates/main Sources
  404 Not Found [IP: 91.189.88.30 80]
Err http://ca.archive.ubuntu.com jaunty-updates/multiverse Sources
  404 Not Found [IP: 91.189.88.30 80]
Err http://ca.archive.ubuntu.com jaunty-updates/universe Sources
  404 Not Found [IP: 91.189.88.30 80]
Err http://ca.archive.ubuntu.com jaunty-updates/universe Packages
  404 Not Found [IP: 91.189.88.30 80]
Err http://ca.archive.ubuntu.com jaunty-updates/multiverse Packages
  404 Not Found [IP: 91.189.88.30 80]
Err http://ca.archive.ubuntu.com jaunty-backports/main Packages
  404 Not Found [IP: 91.189.88.30 80]
Err http://ca.archive.ubuntu.com jaunty-backports/restricted Packages
  404 Not Found [IP: 91.189.88.30 80]
Err http://ca.archive.ubuntu.com jaunty-backports/universe Packages
  404 Not Found [IP: 91.189.88.30 80]
Hit http://packages.medibuntu.org jaunty/non-free Sources
Err http://ca.archive.ubuntu.com jaunty-backports/multiverse Packages
  404 Not Found [IP: 91.189.88.30 80]
Err http://ca.archive.ubuntu.com jaunty-backports/main Sources
  404 Not Found [IP: 91.189.88.30 80]
Err http://ca.archive.ubuntu.com jaunty-backports/restricted Sources
  404 Not Found [IP: 91.189.88.30 80]
Err http://ca.archive.ubuntu.com jaunty-backports/universe Sources
  404 Not Found [IP: 91.189.88.30 80]
Err http://ca.archive.ubuntu.com jaunty-backports/multiverse Sources
  404 Not Found [IP: 91.189.88.30 80]
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/source/Sources  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/source/Sources  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/source/Sources  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/source/Sources  404 Not Found [IP: 91.189.88.30 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
***@***:~$ 


```

---

### Post by mc4man on 2011-07-09
Jaunty is end of life and those repos are gone, waiting will do no good.
If wanting to continue using jaunty then search out how to switch to the old-release repos

---

### Post by rudedcam on 2011-07-10
> Jaunty is end of life and those repos are gone, waiting will do no good.
If wanting to continue using jaunty then search out how to switch to the old-release repos
that's what i feared. i'll update to the latest instead.
thanks for the heads up!

---

### Post by jp19online on 2011-07-24
Hi,

 I am getting similar errors. How do I change from jaunty to something else? (What should I change it to.. where!). Please help... totally unfamiliar with this.

thanks
JP

---

### Post by westie457 on 2011-07-24
> **jp19online said:**
> Hi,

 I am getting similar errors. How do I change from jaunty to something else? (What should I change it to.. where!). Please help... totally unfamiliar with this.

thanks
JP

Easiest route: Back up your personal files (docs music pictures whatever) to somewhere safe. Done that? Good.

Now download a new ISO (10.04.2 LTS) is a good place to start or 11.04 (be aware that you might have issues with hardware).

Create a LiveCD\USB and do a clean install.

---

### Post by mkljun on 2011-11-23
You don't need to download the ISO and install from scratch.

To upgrade a really old releases, you first need to edit your sources.list and change all (xx.)archive.ubuntu.com to old-releases.ubuntu.com.

```
sudo emacs /etc/apt/sources.list
```

So your lines should instead of 

```
deb http://archive.ubuntu.com/ubuntu jaunty main restricted universe
```

look like 

```
deb http://old-releases.ubuntu.com/ubuntu jaunty main restricted universe
```

In this example I use jaunty release. But it works the same on other releases.

Now update the repos

```
sudo apt-get update
```

Install update-manager-core if it is not yet installed:

```
sudo apt-get install update-manager-core
```

And now upgrade your system. 

```
sudo do-release-upgrade
```

Note that you can just upgrade to the next release (in my example from 9.04 to 9.10 or from LTS 8.04 to 10.04).

Also note that if upgrading over the ssh session it is advised to run the upgrade in the screen. So if the ssh session drops, the upgrade will continue. Install screen first (if not yet installed)

```
sudo apt-get install screen
```

Now run screen

```
screen
```

And upgrade with 

```
sudo do-release-upgrade
```

How to return to the screen is beyond this post.

lp mk

---

