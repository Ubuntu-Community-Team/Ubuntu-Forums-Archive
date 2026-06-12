---
title: "Vineyard with Ubuntu 11.10 not installing"
date: 2012-02-17
forum: General Help
---

### Post by HomesteadMommy on 2012-02-17
I'm trying to install vineyard using the info on their download page [http://vineyardproject.org/download/](http://vineyardproject.org/download/)  .  I've tried a few times but keep getting the error below.  Has anyone been able to get it working?
I also tried entering the ppa's in the software center.  This should show vineyard when I then search for it right?  But it doesn't.

Thanks!

```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.znWQEzBaJq --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 79E3BFF61556818AFD15688E150BA781A5FF2BFC
gpg: requesting key A5FF2BFC from hkp server keyserver.ubuntu.com
gpg: key A5FF2BFC: "Launchpad gnome-wine" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://security.ubuntu.com oneiric-security InRelease            
Ign http://archive.ubuntu.com oneiric InRelease                      
Ign http://archive.ubuntu.com oneiric-updates InRelease
Ign http://archive.canonical.com oneiric InRelease
Ign http://ppa.launchpad.net oneiric Release.gpg                     
Hit http://security.ubuntu.com oneiric-security Release.gpg          
Hit http://archive.ubuntu.com oneiric Release.gpg                    
Hit http://archive.canonical.com oneiric Release.gpg                 
Hit http://ppa.launchpad.net oneiric Release.gpg                     
Hit http://security.ubuntu.com oneiric-security Release              
Hit http://archive.canonical.com oneiric Release                               
Get:1 http://archive.ubuntu.com oneiric-updates Release.gpg [198 B]            
Ign http://ppa.launchpad.net oneiric Release                                   
Hit http://archive.ubuntu.com oneiric Release                                  
Hit http://security.ubuntu.com oneiric-security/main amd64 Packages            
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Get:2 http://archive.ubuntu.com oneiric-updates Release [40.8 kB]              
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://security.ubuntu.com oneiric-security/restricted amd64 Packages      
Hit http://security.ubuntu.com oneiric-security/universe amd64 Packages        
Hit http://security.ubuntu.com oneiric-security/multiverse amd64 Packages      
Hit http://security.ubuntu.com oneiric-security/main i386 Packages             
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages       
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages         
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages       
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex          
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex    
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex      
Hit http://security.ubuntu.com oneiric-security/main Translation-en            
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Hit http://archive.ubuntu.com oneiric/main amd64 Packages                      
Hit http://archive.ubuntu.com oneiric/restricted amd64 Packages                
Hit http://archive.ubuntu.com oneiric/universe amd64 Packages                  
Hit http://archive.ubuntu.com oneiric/multiverse amd64 Packages                
Hit http://archive.ubuntu.com oneiric/main i386 Packages                       
Hit http://archive.ubuntu.com oneiric/restricted i386 Packages                 
Hit http://archive.ubuntu.com oneiric/universe i386 Packages                   
Hit http://archive.ubuntu.com oneiric/multiverse i386 Packages                 
Hit http://archive.ubuntu.com oneiric/main TranslationIndex                    
Hit http://archive.ubuntu.com oneiric/multiverse TranslationIndex              
Hit http://security.ubuntu.com oneiric-security/universe Translation-en        
Hit http://archive.ubuntu.com oneiric/restricted TranslationIndex    
Hit http://archive.ubuntu.com oneiric/universe TranslationIndex      
Get:3 http://archive.ubuntu.com oneiric-updates/main amd64 Packages [288 kB]
Err http://ppa.launchpad.net oneiric/main Sources                              
  404  Not Found
Err http://ppa.launchpad.net oneiric/main amd64 Packages                       
  404  Not Found
Err http://ppa.launchpad.net oneiric/main i386 Packages                       
  404  Not Found
Ign http://archive.canonical.com oneiric/partner Translation-en_US            
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Ign http://archive.canonical.com oneiric/partner Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Ign http://ppa.launchpad.net oneiric/main Translation-en
Get:4 http://archive.ubuntu.com oneiric-updates/restricted amd64 Packages [2,982 B]
Get:5 http://archive.ubuntu.com oneiric-updates/universe amd64 Packages [96.3 kB]
Get:6 http://archive.ubuntu.com oneiric-updates/multiverse amd64 Packages [6,218 B]
Get:7 http://archive.ubuntu.com oneiric-updates/main i386 Packages [288 kB]
Get:8 http://archive.ubuntu.com oneiric-updates/restricted i386 Packages [2,968 B]
Get:9 http://archive.ubuntu.com oneiric-updates/universe i386 Packages [96.6 kB]
Get:10 http://archive.ubuntu.com oneiric-updates/multiverse i386 Packages [6,355 B]
Get:11 http://archive.ubuntu.com oneiric-updates/main TranslationIndex [74 B]  
Get:12 http://archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [72 B]
Get:13 http://archive.ubuntu.com oneiric-updates/restricted TranslationIndex [71 B]
Get:14 http://archive.ubuntu.com oneiric-updates/universe TranslationIndex [73 B]
Hit http://archive.ubuntu.com oneiric/main Translation-en                      
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en                
Hit http://archive.ubuntu.com oneiric/restricted Translation-en                
Hit http://archive.ubuntu.com oneiric/universe Translation-en                  
Hit http://archive.ubuntu.com oneiric-updates/main Translation-en              
Hit http://archive.ubuntu.com oneiric-updates/multiverse Translation-en        
Hit http://archive.ubuntu.com oneiric-updates/restricted Translation-en        
Hit http://archive.ubuntu.com oneiric-updates/universe Translation-en          
Fetched 829 kB in 10s (75.6 kB/s)                                              
W: Failed to fetch http://ppa.launchpad.net/cybolic/vineyard-testing/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/cybolic/vineyard-testing/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/cybolic/vineyard-testing/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package vineyard

```

---

### Post by RockMumbles on 2012-02-18
It doesn't look like 11.10 has a package in the PPA, but this method should work:

Development source
If you would like to test the latest development version, you can download it from Launchpad by running the following commands:
Make sure you have Bazaar installed:

sudo apt-get install bzr

Download the latest source code:

bzr branch lp:vineyard

To actually run this development version, use these commands:
Go to the directory of the source:

cd vineyard

Open Vineyard Preferences:

./vineyard-preferences

---

