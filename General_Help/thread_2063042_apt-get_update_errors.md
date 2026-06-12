---
title: "apt-get update errors"
date: 2012-09-26
forum: General Help
---

### Post by TheFlanman91 on 2012-09-26
Having a problem running sudo apt-get update.

This is what I get when I run it.

```
conor@Conor-Laptop:~$ sudo apt-get update
Ign http://ie.archive.ubuntu.com precise InRelease
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://packages.mate-desktop.org precise InRelease                         
Ign http://ie.archive.ubuntu.com precise-updates InRelease                     
Ign http://archive.canonical.com precise InRelease                             
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ie.archive.ubuntu.com precise-backports InRelease                   
Ign http://security.ubuntu.com precise-security InRelease                      
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://ie.archive.ubuntu.com precise Release.gpg                           
Hit http://ie.archive.ubuntu.com precise-updates Release.gpg                   
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://packages.mate-desktop.org precise/main Sources                      
Hit http://ie.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://ie.archive.ubuntu.com precise Release                               
Hit http://ie.archive.ubuntu.com precise-updates Release                       
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://packages.mate-desktop.org precise/main i386 Packages                
Hit http://ie.archive.ubuntu.com precise-backports Release                     
Hit http://ie.archive.ubuntu.com precise/main Sources                          
Hit http://ie.archive.ubuntu.com precise/restricted Sources                    
Hit http://ie.archive.ubuntu.com precise/universe Sources                      
Hit http://ie.archive.ubuntu.com precise/multiverse Sources                    
Get:2 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://ie.archive.ubuntu.com precise/main i386 Packages                    
Hit http://ie.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://ie.archive.ubuntu.com precise/universe i386 Packages                
Hit http://extras.ubuntu.com precise Release                                   
Ign http://packages.mate-desktop.org precise/main TranslationIndex             
Hit http://ie.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://archive.canonical.com precise Release                               
Hit http://ie.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://ie.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://ie.archive.ubuntu.com precise/restricted TranslationIndex           
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://ie.archive.ubuntu.com precise/universe TranslationIndex             
Hit http://ie.archive.ubuntu.com precise-updates/main Sources                  
Hit http://ie.archive.ubuntu.com precise-updates/restricted Sources            
Hit http://ie.archive.ubuntu.com precise-updates/universe Sources              
Hit http://ie.archive.ubuntu.com precise-updates/multiverse Sources            
Hit http://ie.archive.ubuntu.com precise-updates/main i386 Packages            
Hit http://ie.archive.ubuntu.com precise-updates/restricted i386 Packages      
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://ie.archive.ubuntu.com precise-updates/universe i386 Packages        
Hit http://ie.archive.ubuntu.com precise-updates/multiverse i386 Packages      
Hit http://archive.canonical.com precise/partner i386 Packages                 
Hit http://ie.archive.ubuntu.com precise-updates/main TranslationIndex         
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://ie.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://ie.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://ie.archive.ubuntu.com precise-updates/universe TranslationIndex     
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://ie.archive.ubuntu.com precise-backports/main Sources                
Hit http://ie.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://ie.archive.ubuntu.com precise-backports/universe Sources            
Hit http://ie.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://ie.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://ie.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://ie.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://ie.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Ign http://ppa.launchpad.net precise InRelease                                 
Get:3 http://security.ubuntu.com precise-security/main Sources [45.3 kB]       
Ign http://ppa.launchpad.net precise InRelease                                 
Get:4 http://ppa.launchpad.net precise Release.gpg [316 B]                     
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:5 http://security.ubuntu.com precise-security/restricted Sources [1,950 B] 
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:6 http://security.ubuntu.com precise-security/universe Sources [13.5 kB]   
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:7 http://security.ubuntu.com precise-security/multiverse Sources [1,386 B] 
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:8 http://security.ubuntu.com precise-security/main i386 Packages [171 kB]  
Ign http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release                                   
Ign http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Ign http://ppa.launchpad.net precise Release                                   
Get:9 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:10 http://security.ubuntu.com precise-security/universe i386 Packages [45.3 kB]
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Ign http://ppa.launchpad.net precise/main Sources/DiffIndex                    
Get:11 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,369 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Ign http://extras.ubuntu.com precise/main Translation-en_GB                    
Ign http://archive.canonical.com precise/partner Translation-en_GB             
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://packages.mate-desktop.org precise/main Translation-en_GB            
Ign http://ppa.launchpad.net precise/main i386 Packages/DiffIndex              
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://packages.mate-desktop.org precise/main Translation-en               
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex            
Hit http://ppa.launchpad.net precise/main Sources                     
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex            
Hit http://ppa.launchpad.net precise/main Sources                     
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex            
Hit http://ppa.launchpad.net precise/main Sources                     
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ie.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://ie.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://ie.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://ie.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://ie.archive.ubuntu.com precise/main Translation-en_GB       
Hit http://ie.archive.ubuntu.com precise/main Translation-en               
Hit http://ie.archive.ubuntu.com precise/multiverse Translation-en_GB      
Hit http://ie.archive.ubuntu.com precise/multiverse Translation-en         
Hit http://ie.archive.ubuntu.com precise/restricted Translation-en_GB 
Hit http://ie.archive.ubuntu.com precise/restricted Translation-en    
Hit http://ie.archive.ubuntu.com precise/universe Translation-en_GB   
Hit http://ie.archive.ubuntu.com precise/universe Translation-en      
Ign http://ppa.launchpad.net precise/main TranslationIndex            
Hit http://ie.archive.ubuntu.com precise-updates/main Translation-en_GB
Hit http://ie.archive.ubuntu.com precise-updates/main Translation-en  
Hit http://ie.archive.ubuntu.com precise-updates/multiverse Translation-en_GB
Hit http://ie.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://ie.archive.ubuntu.com precise-updates/restricted Translation-en_GB
Hit http://security.ubuntu.com precise-security/main Translation-en   
Hit http://ie.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://ppa.launchpad.net precise/main Sources                     
Hit http://ie.archive.ubuntu.com precise-updates/universe Translation-en_GB
Hit http://ie.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://ie.archive.ubuntu.com precise-backports/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://ppa.launchpad.net precise/main i386 Packages               
Hit http://ie.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://ie.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://ie.archive.ubuntu.com precise-backports/universe Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Ign http://ppa.launchpad.net precise/main TranslationIndex            
Hit http://security.ubuntu.com precise-security/universe Translation-en    
Hit http://ppa.launchpad.net precise/main Sources                          
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Err http://ppa.launchpad.net precise/main Sources
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net precise/main Translation-en_GB
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_GB
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_GB
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_GB
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_GB
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_GB
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_GB
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_GB
Ign http://ppa.launchpad.net precise/main Translation-en
Fetched 335 kB in 4s (77.3 kB/s)
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C2518248EEA14886
W: Failed to fetch http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Sorry but i'm a complete noob. Just not sure how to get rid of the sources or "fetch" them.

Can anyone help?

---

### Post by drmrgd on 2012-09-26
Did you recently perform a system upgrade?  I had a look at that PPA, and it looks like there is no Precise repository listed (the most recent in there is Natty (AKA 11.04).  This is why you're getting the Not Found error, as a repository doesn't exist for 12.04.  I'm not sure which package you're using from that repo.  But, in order to fix the problem, you'll just have to remove that source from your sources list either in the Software Center or from the terminal by removing the entry from either /etc/apt/sources.list or the file from /etc/apt.sources.list.d/.  

Here's some Documentation on how to add and remove repositories in Ubuntu:

[https://help.ubuntu.com/community/SourcesList](https://help.ubuntu.com/community/SourcesList)

---

### Post by TheFlanman91 on 2012-09-26
Thanks very much for the quick reply.

No I actually clean installed 12.04 from the liveCD. I did however mess around with it a lot. Got KDE and Cinnamon and a few other Desktop Environments to play around with them. I'm now using Gnome 3 not Unity. I don't know if that makes a difference. Thanks I'll take a look at that link now :)

---

### Post by TheFlanman91 on 2012-09-26
I'm not quite sure which repo you mean? Which sources should I remove?

---

### Post by drmrgd on 2012-09-26
I'm not exactly sure where you put those repository links.  Would you mind posting the following:

```
cat /etc/apt/sources.list
```

```
ls /etc/apt/sources.list.d/
```

That will show me where that entry is and help tell you which to delete.

---

### Post by HiImTye on 2012-09-27
you're getting a 404 on this PPA:
[https://launchpad.net/~pmcenery/+archive/ppa/+index?field.series_filter=karmic](https://launchpad.net/~pmcenery/+archive/ppa/+index?field.series_filter=karmic)
to remove it, use:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:pmcenery/ppa
sudo apt-get update
```

---

