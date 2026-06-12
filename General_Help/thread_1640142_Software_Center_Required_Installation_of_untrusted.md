---
title: "Software Center Required Installation of untrusted Packages"
date: 2010-12-07
forum: General Help
---

### Post by RiThePirate on 2010-12-07
So as i have stated above whenever I try to install any software from the Ubuntu Software Center I get that error... I ran sudo apt-get update (as I saw someone in a different thread had suggested) and came up with this:

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release                                 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Err [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
  Connection failed
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
  Connection failed
Err [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
  Connection failed
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US    
  Connection failed
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources/DiffIndex                   
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages/DiffIndex            
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages                      
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Err [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
  Connection failed
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages                      
Err [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages               
  Connection failed
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
  Connection failed
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages                      
  Connection failed
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources            
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en  
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
  Connection failed [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
  Connection failed [IP: 91.189.92.167 80]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources                     
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
  Connection failed [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
  Connection failed [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
  Connection failed [IP: 91.189.92.167 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources
  403  Forbidden [IP: 91.189.92.169 80]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources/DiffIndex        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources/DiffIndex  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources                    
  403  Forbidden [IP: 91.189.92.170 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources/DiffIndex    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main amd64 Packages/DiffIndex 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse amd64 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg
  Connection failed [IP: 91.189.88.30 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources           
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en 
  Connection failed [IP: 91.189.88.40 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources             
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
  Connection failed [IP: 91.189.88.46 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main amd64 Packages
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
  Connection failed [IP: 91.189.92.170 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted amd64 Packages     
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
  Connection failed [IP: 91.189.88.30 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe amd64 Packages       
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
  Connection failed [IP: 91.189.88.40 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse amd64 Packages     
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
  Connection failed [IP: 91.189.88.46 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
  Connection failed [IP: 91.189.92.170 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
  Connection failed [IP: 91.189.88.30 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe amd64 Packages       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse amd64 Packages     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources/DiffIndex
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources
  Connection failed [IP: 91.189.92.166 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main amd64 Packages/DiffIndex        
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
  Connection failed [IP: 91.189.88.37 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted amd64 Packages/DiffIndex
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources            
  Connection failed [IP: 91.189.92.167 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe amd64 Packages/DiffIndex    
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources              
  403  Forbidden [IP: 91.189.88.37 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse amd64 Packages/DiffIndex  
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main amd64 Packages
  Connection failed [IP: 91.189.92.166 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources/DiffIndex
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted amd64 Packages   
  Connection failed [IP: 91.189.88.37 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources/DiffIndex
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe amd64 Packages      
  Connection failed [IP: 91.189.92.167 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources/DiffIndex
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse amd64 Packages     
  Connection failed [IP: 91.189.92.166 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources/DiffIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main amd64 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted amd64 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe amd64 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse amd64 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse amd64 Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources
  Connection failed [IP: 91.189.88.40 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources
  Connection failed [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
  Connection failed [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
  Connection failed [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main amd64 Packages
  Connection failed [IP: 91.189.88.40 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted amd64 Packages
  Connection failed [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe amd64 Packages
  Connection failed [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse amd64 Packages
  403  Forbidden [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources
  Connection failed [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources
  Connection failed [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources
  Connection failed [IP: 91.189.92.169 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources
  Connection failed [IP: 91.189.92.171 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main amd64 Packages
  Connection failed [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted amd64 Packages
  403  Forbidden [IP: 91.189.88.40 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe amd64 Packages
  Connection failed [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse amd64 Packages
  Connection failed [IP: 91.189.92.169 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg)  Connection failed [IP: 91.189.88.30 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2)  Connection failed [IP: 91.189.88.40 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2)  Connection failed [IP: 91.189.88.46 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2)  Connection failed [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2)  Connection failed [IP: 91.189.88.30 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2)  Connection failed [IP: 91.189.88.40 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2)  Connection failed [IP: 91.189.88.46 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2)  Connection failed [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2)  Connection failed [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2](http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_US.bz2)  Connection failed [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2)  Connection failed [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_US.bz2)  Connection failed [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2)  Connection failed [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_US.bz2)  Connection failed [IP: 91.189.92.167 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.gz)  Connection failed

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-amd64/Packages.gz](http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  Connection failed

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  403  Forbidden [IP: 91.189.92.169 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz)  403  Forbidden [IP: 91.189.92.170 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz)  Connection failed [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz)  Connection failed [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz)  Connection failed [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz)  403  Forbidden [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-amd64/Packages.gz)  Connection failed [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-amd64/Packages.gz)  Connection failed [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-amd64/Packages.gz)  Connection failed [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-amd64/Packages.gz)  Connection failed [IP: 91.189.92.166 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz)  Connection failed [IP: 91.189.88.40 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  Connection failed [IP: 91.189.88.46 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz)  Connection failed [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz)  Connection failed [IP: 91.189.88.30 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Connection failed [IP: 91.189.88.40 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-amd64/Packages.gz)  Connection failed [IP: 91.189.88.46 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-amd64/Packages.gz)  Connection failed [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-amd64/Packages.gz)  403  Forbidden [IP: 91.189.88.30 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz)  Connection failed [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz)  Connection failed [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz)  Connection failed [IP: 91.189.92.169 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz)  Connection failed [IP: 91.189.92.171 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-amd64/Packages.gz)  Connection failed [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-amd64/Packages.gz)  403  Forbidden [IP: 91.189.88.40 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-amd64/Packages.gz)  Connection failed [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-amd64/Packages.gz)  Connection failed [IP: 91.189.92.169 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by zvacet on 2010-12-07
Under Ubuntu software center>edit>repositories> change server to main and see if that helps.

---

