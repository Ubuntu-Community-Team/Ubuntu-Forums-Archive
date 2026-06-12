---
title: "Possible Network Prolems"
date: 2010-02-21
forum: General Help
---

### Post by crazyness003 on 2010-02-21
Hi all,
 I recently noticed that I'm having bizarre results with my internet connection, specifically pertaining to APT. When I "sudo apt-get update" This is the result I get with ANY SERVER SELECTED. I tried the fastest server, one closer to me, a random one and the main server, they all yield the same result
```
Hit http://packages.medibuntu.org karmic Release.gpg                                                                                               
Ign http://packages.medibuntu.org karmic/free Translation-en_US                                                                                    
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US                                                                                
Hit http://packages.medibuntu.org karmic Release                                                                                                   
Hit http://packages.medibuntu.org karmic/free Packages                                                                                             
Hit http://packages.medibuntu.org karmic/non-free Packages                                                                                         
Hit http://packages.medibuntu.org karmic/free Sources                                                                                              
Hit http://packages.medibuntu.org karmic/non-free Sources                                                                                          
Ign http://deb.playonlinux.com karmic Release.gpg                                                                                                  
Ign http://deb.playonlinux.com karmic/main Translation-en_US                                                                                       
Get:1 http://deb.playonlinux.com karmic Release [1,723B]                                                                                                    
Ign http://deb.playonlinux.com karmic/main Packages                                                                                                         
Ign http://deb.playonlinux.com karmic/main Packages                                                                                                         
Hit http://deb.playonlinux.com karmic/main Packages                                                                                                         
Hit http://download.virtualbox.org karmic Release.gpg                                                                                                       
Ign http://download.virtualbox.org karmic/non-free Translation-en_US                                                                                        
Hit http://download.virtualbox.org karmic Release                                                                                                           
Hit http://download.virtualbox.org karmic/non-free Packages                                                                                                 
Hit http://archive.ubuntu.com karmic Release.gpg                                                                                                            
Ign http://archive.ubuntu.com karmic/main Translation-en_US                                                                                                 
Ign http://archive.ubuntu.com karmic/restricted Translation-en_US                                                                                           
Ign http://archive.ubuntu.com karmic/universe Translation-en_US                                                                                             
Ign http://archive.ubuntu.com karmic/multiverse Translation-en_US                                                                                           
Hit http://archive.ubuntu.com karmic-updates Release.gpg                                                                                                    
Ign http://archive.ubuntu.com karmic-updates/main Translation-en_US                                                                                         
Ign http://archive.ubuntu.com karmic-updates/restricted Translation-en_US                                                                                   
Ign http://archive.ubuntu.com karmic-updates/universe Translation-en_US                                                                                     
Ign http://archive.ubuntu.com karmic-updates/multiverse Translation-en_US                                                                                   
Hit http://archive.ubuntu.com karmic-security Release.gpg                                                                                                   
Ign http://archive.ubuntu.com karmic-security/main Translation-en_US                                                                                        
Ign http://archive.ubuntu.com karmic-security/restricted Translation-en_US                                                                                  
Ign http://archive.ubuntu.com karmic-security/universe Translation-en_US                                                                                    
Ign http://archive.ubuntu.com karmic-security/multiverse Translation-en_US                                                                                  
Hit http://archive.ubuntu.com karmic-proposed Release.gpg                                                                                                   
Ign http://archive.ubuntu.com karmic-proposed/restricted Translation-en_US                                                                                  
Ign http://archive.ubuntu.com karmic-proposed/main Translation-en_US                                                                                        
Ign http://archive.ubuntu.com karmic-proposed/multiverse Translation-en_US                                                                                  
Ign http://archive.ubuntu.com karmic-proposed/universe Translation-en_US                                                                                    
Hit http://archive.ubuntu.com karmic-backports Release.gpg                                                                                                  
Ign http://archive.ubuntu.com karmic-backports/restricted Translation-en_US                                                                                 
Ign http://archive.ubuntu.com karmic-backports/main Translation-en_US                                                                                       
Ign http://archive.ubuntu.com karmic-backports/multiverse Translation-en_US                                                                                 
Ign http://archive.ubuntu.com karmic-backports/universe Translation-en_US                                                                                   
Hit http://archive.ubuntu.com karmic Release                                                                                                                
Hit http://archive.ubuntu.com karmic-updates Release                                                                                                        
Hit http://archive.ubuntu.com karmic-security Release                                                                                                       
Hit http://archive.ubuntu.com karmic-proposed Release                                                                                                       
Hit http://archive.ubuntu.com karmic-backports Release                                                                                                      
Hit http://archive.ubuntu.com karmic/restricted Sources                                                                                                     
Hit http://archive.ubuntu.com karmic/main Sources                                                                                                           
Hit http://archive.ubuntu.com karmic/main Packages                                                                                                          
Hit http://archive.ubuntu.com karmic/restricted Packages                                                                                                    
Hit http://archive.ubuntu.com karmic/multiverse Sources                                                                                                     
Hit http://archive.ubuntu.com karmic/universe Sources                                                                                                       
Hit http://archive.ubuntu.com karmic/universe Packages                                                                                                      
Hit http://archive.ubuntu.com karmic/multiverse Packages                                                                                                    
Hit http://archive.ubuntu.com karmic-updates/main Packages                                                                                                  
Hit http://archive.ubuntu.com karmic-updates/restricted Packages                                                                                            
Hit http://archive.ubuntu.com karmic-updates/restricted Sources                                                                                             
Hit http://archive.ubuntu.com karmic-updates/main Sources                                                                                                   
Hit http://archive.ubuntu.com karmic-updates/multiverse Sources                                                                                             
Hit http://archive.ubuntu.com karmic-updates/universe Sources                                                                                               
Hit http://archive.ubuntu.com karmic-updates/universe Packages                                                                                              
Hit http://archive.ubuntu.com karmic-updates/multiverse Packages                                                                                            
Hit http://archive.ubuntu.com karmic-security/main Packages                                                                                                 
Hit http://archive.ubuntu.com karmic-security/restricted Packages                                                                                           
Hit http://archive.ubuntu.com karmic-security/restricted Sources                                                                                            
Hit http://archive.ubuntu.com karmic-security/main Sources                                                                                                  
Hit http://archive.ubuntu.com karmic-security/multiverse Sources                                                                                            
Hit http://archive.ubuntu.com karmic-security/universe Sources                                                                                              
Hit http://archive.ubuntu.com karmic-security/universe Packages                                                                                             
Hit http://archive.ubuntu.com karmic-security/multiverse Packages                                                                                           
Hit http://archive.ubuntu.com karmic-proposed/restricted Packages                                                                                           
Hit http://archive.ubuntu.com karmic-proposed/main Packages                                                                                                 
Hit http://archive.ubuntu.com karmic-proposed/multiverse Packages                                                                                           
Hit http://archive.ubuntu.com karmic-proposed/universe Packages                                                                                             
Hit http://archive.ubuntu.com karmic-proposed/restricted Sources                                                                                            
Hit http://archive.ubuntu.com karmic-proposed/main Sources                                                                                                  
Hit http://archive.ubuntu.com karmic-proposed/multiverse Sources                                                                                            
Hit http://archive.ubuntu.com karmic-proposed/universe Sources                                                                                              
Hit http://archive.ubuntu.com karmic-backports/restricted Packages                                                                                          
Hit http://archive.ubuntu.com karmic-backports/main Packages                                                                                                
Hit http://archive.ubuntu.com karmic-backports/multiverse Packages                                                                                          
Hit http://archive.ubuntu.com karmic-backports/universe Packages                                                                                            
Hit http://archive.ubuntu.com karmic-backports/restricted Sources                                                                                           
Hit http://archive.ubuntu.com karmic-backports/main Sources                                                                                                 
Hit http://archive.ubuntu.com karmic-backports/multiverse Sources                                                                                           
Hit http://archive.ubuntu.com karmic-backports/universe Sources                                                                                             
Hit http://ppa.launchpad.net karmic Release.gpg                                                                                                             
Ign http://ppa.launchpad.net karmic/main Translation-en_US                                                                                                  
Hit http://ppa.launchpad.net karmic Release.gpg                                                                                                             
Ign http://ppa.launchpad.net karmic/main Translation-en_US                                                                                                  
Hit http://ppa.launchpad.net karmic Release.gpg                                                                                                             
Ign http://ppa.launchpad.net karmic/main Translation-en_US                                                                                                  
Hit http://ppa.launchpad.net jaunty Release.gpg                                                                                                             
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                                                                                                  
Hit http://ppa.launchpad.net jaunty Release.gpg                                                                                                             
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                                                                                                  
Hit http://ppa.launchpad.net karmic Release.gpg                                                                                                             
Ign http://ppa.launchpad.net karmic/main Translation-en_US                                                                                                  
Hit http://ppa.launchpad.net karmic Release.gpg                                                                                                             
Ign http://ppa.launchpad.net karmic/main Translation-en_US                                                                                                  
Hit http://ppa.launchpad.net karmic Release                                                                                                                 
Hit http://ppa.launchpad.net karmic Release                                                                                                                 
Hit http://ppa.launchpad.net karmic Release                                                                                                                 
Hit http://ppa.launchpad.net jaunty Release                                                                                                                 
Hit http://ppa.launchpad.net jaunty Release                                                                                                                 
Hit http://ppa.launchpad.net karmic Release                                                                                                                 
Hit http://ppa.launchpad.net karmic Release                                                                                                                 
Hit http://ppa.launchpad.net karmic/main Packages                                                                                                           
Hit http://ppa.launchpad.net karmic/main Packages                                                                                                           
Hit http://ppa.launchpad.net karmic/main Sources                                                                                                            
Hit http://ppa.launchpad.net karmic/main Packages                                                                                                           
Hit http://ppa.launchpad.net karmic/main Sources                                                                                                            
Hit http://ppa.launchpad.net jaunty/main Packages                                                                                                           
Hit http://ppa.launchpad.net jaunty/main Sources                                                                                                            
Hit http://ppa.launchpad.net jaunty/main Packages                                                                                                           
Hit http://ppa.launchpad.net jaunty/main Sources                                                                                                            
Hit http://ppa.launchpad.net karmic/main Packages                                                                                                           
Hit http://ppa.launchpad.net karmic/main Packages                                                                                                           
Get:2 http://dl.google.com stable Release.gpg [189B]                                                                                                        
Ign http://dl.google.com stable/main Translation-en_US                                                                                    
Get:3 http://dl.google.com stable Release [2,540B]                                                                                
Get:4 http://dl.google.com stable/main Packages [871B]                                                      
Err http://deb.opera.com stable Release.gpg                                                                 
  Could not resolve 'deb.opera.com'
Err http://deb.opera.com stable/non-free Translation-en_US                                                  
  Could not resolve 'deb.opera.com'
Err http://archive.canonical.com karmic Release.gpg                                                                                                         
  Could not resolve 'archive.canonical.com'
Err http://archive.canonical.com karmic/partner Translation-en_US                                                                                           
  Could not resolve 'archive.canonical.com'
Err http://linux.getdropbox.com karmic Release.gpg                                                                                                          
  Could not resolve 'linux.getdropbox.com'
Err http://linux.getdropbox.com karmic/main Translation-en_US
  Could not resolve 'linux.getdropbox.com'
Fetched 3,601B in 40s (90B/s)           
Reading package lists... Done
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg  Could not resolve 'archive.canonical.com'

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_US.bz2  Could not resolve 'archive.canonical.com'

W: Failed to fetch http://deb.opera.com/opera/dists/stable/Release.gpg  Could not resolve 'deb.opera.com'

W: Failed to fetch http://deb.opera.com/opera/dists/stable/non-free/i18n/Translation-en_US.bz2  Could not resolve 'deb.opera.com'

W: Failed to fetch http://linux.getdropbox.com/ubuntu/dists/karmic/Release.gpg  Could not resolve 'linux.getdropbox.com'

W: Failed to fetch http://linux.getdropbox.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2  Could not resolve 'linux.getdropbox.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.

```After I change a Software Source Download location, and reloading the index, this error occures
```
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg  Could not resolve 'archive.canonical.com'

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_US.bz2  Could not resolve 'archive.canonical.com'

W: Failed to fetch http://dl.google.com/linux/deb/dists/stable/Release.gpg  Could not resolve 'dl.google.com'

W: Failed to fetch http://dl.google.com/linux/deb/dists/stable/main/i18n/Translation-en_US.bz2  Could not resolve 'dl.google.com'

W: Failed to fetch http://deb.opera.com/opera/dists/stable/Release.gpg  Could not resolve 'deb.opera.com'

W: Failed to fetch http://deb.opera.com/opera/dists/stable/non-free/i18n/Translation-en_US.bz2  Could not resolve 'deb.opera.com'

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic/restricted/source/Sources.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic/main/binary-amd64/Packages.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic/restricted/binary-amd64/Packages.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic/multiverse/source/Sources.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic/universe/source/Sources.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic/universe/binary-amd64/Packages.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic/multiverse/binary-amd64/Packages.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-updates/main/binary-amd64/Packages.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-updates/restricted/binary-amd64/Packages.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-updates/restricted/source/Sources.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-updates/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-updates/multiverse/source/Sources.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-updates/universe/source/Sources.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-updates/universe/binary-amd64/Packages.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-updates/multiverse/binary-amd64/Packages.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-security/main/binary-amd64/Packages.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-security/restricted/binary-amd64/Packages.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-security/restricted/source/Sources.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-security/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-security/multiverse/source/Sources.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-security/universe/source/Sources.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-security/universe/binary-amd64/Packages.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-security/multiverse/binary-amd64/Packages.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-proposed/restricted/binary-amd64/Packages.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-proposed/main/binary-amd64/Packages.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-proposed/multiverse/binary-amd64/Packages.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-proposed/universe/binary-amd64/Packages.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-proposed/restricted/source/Sources.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-proposed/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-proposed/multiverse/source/Sources.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-proposed/universe/source/Sources.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-backports/restricted/binary-amd64/Packages.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-backports/main/binary-amd64/Packages.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-backports/multiverse/binary-amd64/Packages.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-backports/universe/binary-amd64/Packages.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-backports/restricted/source/Sources.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-backports/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-backports/multiverse/source/Sources.gz  404  Not Found

W: Failed to fetch http://mirror.uoregon.edu/ubuntu/archives/dists/karmic-backports/universe/source/Sources.gz  404  Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.

```I did a search on the forums and found a couple of threads, but they are linked to proxy settings. Mine is directly connected to the internet.

The final "nail-in-the-coffin" symptom was my web experience. I cannot get hulu to play any videos.
```
Sorry, we are unable to stream this video. Please check your internet connection and try again
```And when I started to troubleshoot I went to check my download speed at [www.speedtest.net]("http://www.speedtest.net"), but it gave me an error as well.
```
Download test returned an error while trying to read the download file
```Whereas on [www.auditmypc.com]("http://www.auditmypc.com"), I get fantastic speed results. **See the attachment**. 

I don't know where to start. My specs are Ubuntu 9.10 64 bit. Kernel 2.6.31-20-generic. 
I have concluded that my system is not stable [[see this thread]]("http://ubuntuforums.org/showthread.php?t=1367011") but can that affect my network too?

If anyone has ANY information for me, please let me know.

---

### Post by shrimpy89 on 2010-10-11
Seems that I'm bumping a dead thread here, but I'm having the same problem on both Lucid and Maverick.  Anyone find a fix?

---

### Post by Sef on 2010-10-11
Locked. I will reopen it if the OP wants me to.

Shrimpy89, please start a thread of your own with a copy of your respositories.  Thank you.

---

