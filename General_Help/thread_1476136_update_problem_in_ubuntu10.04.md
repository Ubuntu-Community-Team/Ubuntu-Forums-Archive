---
title: "update problem in ubuntu10.04"
date: 2010-05-07
forum: General Help
---

### Post by konjeng on 2010-05-07
i hav problem when i try to update/install a software in ubuntu 10.04 
please help!!!!
thanks in advance
W: Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz)   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old  ones used instead.
root@ubuntu:/home/brolie# sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 -  No address associated with hostname)
Err [http://archive.canonical.com](http://archive.canonical.com) lucid  Release.gpg                                                                 
  Something wicked happened resolving 'archive.canonical.com:http' (-5 -  No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid  Release.gpg                                                                 
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main  Translation-en_US                                      
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 -  No address associated with hostname)
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner  Translation-en_US                                          
  Something wicked happened resolving 'archive.canonical.com:http' (-5 -  No address associated with hostname)
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main  Translation-en_US                                             
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted  Translation-en_US                                
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 -  No address associated with hostname)
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid  Release                                                                     
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted  Translation-en_US                                       
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe  Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 -  No address associated with hostname)
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner  Packages                                                           
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe  Translation-en_US                                         
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse  Translation-en_US                                
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 -  No address associated with hostname)
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner  Packages                                                           
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse  Translation-en_US                                       
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security  Release                       
Err [http://archive.canonical.com](http://archive.canonical.com) lucid/partner  Packages                       
  Something wicked happened resolving 'archive.canonical.com:http' (-5 -  No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates  Release.gpg                    
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main  Packages                 
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main  Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted  Packages           
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted  Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main  Sources                  
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe  Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted  Sources             
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse  Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe  Packages              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid  Release                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe  Sources               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates  Release                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse  Packages            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main  Packages                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted  Packages                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main  Packages                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main  Sources                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted  Packages            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted  Sources                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main  Sources                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe  Packages                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted  Sources             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe  Sources                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe  Packages              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse  Packages                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 -  No address associated with hostname)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main  Sources                  
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted  Packages            
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 -  No address associated with hostname)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted  Sources            
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main  Sources                   
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 -  No address associated with hostname)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe  Packages             
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted  Sources             
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 -  No address associated with hostname)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe  Sources              
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe  Packages              
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 -  No address associated with hostname)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse  Packages           
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe  Sources               
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 -  No address associated with hostname)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse  Sources            
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse  Packages            
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 -  No address associated with hostname)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main  Packages                         
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse  Sources             
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 -  No address associated with hostname)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)
W: Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Something  wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address  associated with hostname)

W: Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)

W: Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2)   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)

W: Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2)   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)

W: Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2)   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)

W: Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)

W: Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2)   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)

W: Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2)   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)

W: Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2)   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)

W: Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2)   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)

W: Failed to fetch  [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)   Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2)   Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2)   Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2)   Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2)   Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Something  wicked happened resolving 'archive.canonical.com:http' (-5 - No address  associated with hostname)

W: Failed to fetch  [http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_US.bz2)   Something wicked happened resolving 'archive.canonical.com:http' (-5 -  No address associated with hostname)

W: Failed to fetch  [http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz)   Something wicked happened resolving 'archive.canonical.com:http' (-5 -  No address associated with hostname)

W: Failed to fetch  [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz)   Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz)   Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz)   Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz)   Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz)   Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz)   Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz)   Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz)   Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz)   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)

W: Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz)   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)

W: Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz)   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)

W: Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz)   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)

W: Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz)   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)

W: Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz)   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)

W: Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz)   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)

W: Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz)   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)

W: Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)

W: Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz)   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)

W: Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz)   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)

W: Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz)   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)

W: Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz)   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)

W: Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz)   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)

W: Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz)   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)

W: Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz)   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old  ones used instead.
root@ubuntu:/home/brolie# /etc/apt/sources.list 
bash: /etc/apt/sources.list: Permission denied
root@ubuntu:/home/brolie# sudo su
root@ubuntu:/home/brolie# /etc/apt/sources.list 
bash: /etc/apt/sources.list: Permission denied
root@ubuntu:/home/brolie# cd ..
root@ubuntu:/home# cd ..
root@ubuntu:/# cd ..
root@ubuntu:/# /etc/apt/sources.list 
bash: /etc/apt/sources.list: Permission denied
root@ubuntu:/# sudo su
root@ubuntu:/# cat /etc/apt/sources.list
# deb cdrom:[Ubuntu-Netbook 10.04 _Lucid Lynx_ - Release i386  (20100429.4)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade  to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main  restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the  Ubuntu
## team. Also, please note that software in universe WILL NOT receive  any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the  Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as  to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the  'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it  includes
## newer versions of some applications which may provide useful  features.
## Also, please note that software in backports WILL NOT receive any  review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main  restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main  restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and  the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
root@ubuntu:/# sudo nano /etc/apt/sources.list
Use "fg" to return to nano.

[1]+  Stopped                 sudo nano /etc/apt/sources.list
root@ubuntu:/# deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) hardy main 
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
deb: command not found
root@ubuntu:/# cdrom:[description_of_cd]/ 
bash: cdrom:[description_of_cd]/: No such file or directory
root@ubuntu:/# [ftp://ftp.domain.ext/path/to/repository](ftp://ftp.domain.ext/path/to/repository) 
bash: [ftp://ftp.domain.ext/path/to/repository:](ftp://ftp.domain.ext/path/to/repository:) No such file or directory
root@ubuntu:/#  sudo add-apt-repository  ppa:am-monkeyd/nautilus-elementary-ppa
Error reading  [https://launchpad.net/api/1.0/~am-monkeyd/+archive/nautilus-elementary-ppa:](https://launchpad.net/api/1.0/~am-monkeyd/+archive/nautilus-elementary-ppa:)  <urlopen error [Errno -2] Name or service not known>
root@ubuntu:/# sudo add-apt-repository  ppa:am-monkeyd/nautilus-elementary-ppa
Error reading  [https://launchpad.net/api/1.0/~am-monkeyd/+archive/nautilus-elementary-ppa:](https://launchpad.net/api/1.0/~am-monkeyd/+archive/nautilus-elementary-ppa:)  <urlopen error [Errno -2] Name or service not known>
root@ubuntu:/# clear

root@ubuntu:/# sudo apt-get update
Ign cdrom://Ubuntu-Netbook 10.04 _Lucid Lynx_ - Release i386  (20100429.4)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu-Netbook 10.04 _Lucid Lynx_ - Release i386  (20100429.4)/ lucid/restricted Translation-en_US
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid  Release.gpg                                                
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No  address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                         
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)
Err [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/)  lucid/main Translation-en_US
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No  address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US      
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main  Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No  address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted  Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main  Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted  Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)
W: Failed to fetch  [http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Something  wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address  associated with hostname)

W: Failed to fetch  [http://archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)   Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2)   Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)   Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2)   Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2)   Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://archive.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)   Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2)   Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2)   Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/lucid/Release.gpg)   Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)   Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)   Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz)   Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz)   Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz)   Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz)   Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)   Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz)   Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz)   Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz)   Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz)   Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz)   Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz)   Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)

W: Failed to fetch  [http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz)   Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No  address associated with hostname)

E: Some index files failed to download, they have been ignored, or old  ones used instead.
this comes up when i type sudo apt-get update

---

### Post by zuerston on 2010-05-07
Sounds like bad INTERNET connection,its been crummy here all week.
Try it later.

---

### Post by konjeng on 2010-05-08
the net connection is fine 
i don't have any problem accessing the net

---

### Post by linuxluver on 2010-05-10
arggh. i hate linux for this. i ALWAYS get these type of messages when i use it on different networks with a proxy on even one of them. i didn't get these messages on my 10.04 netbook remix until i got home from school (which doesnt have a proxy on its wifi network), and tried to install packages. at home, there is a proxy on our wifi network. when i first installed it at home, i was able to install packages fine without anything messing up (it went through the proxy fine). at school, i was also able to install packages fine. back home, however, changing back to my proxy, i receive these messages. i have had almost this exact problem on EVERY ubuntu system i have installed on one of my machines, and with EVERY version of it, no matter what flavor. i have repeatedly filed bug reports and put this problem to this forum, and no one has paid attention to it. get some help, please. this is a terrible issue plaguing ubuntu, and perhaps linux as a whole. i hope some action will be taken against this. if next version (at most) has not removed this bug, i will never use ubuntu again. i am tired of having to deal with this.

---

### Post by Negr0 on 2010-05-11
Im having the same problem, but i didnt find any solution yet:(

---

### Post by newb85 on 2010-05-16
This problem is *not* specific to 10.04.  I'm also experiencing it on a laptop that's still running 9.10.

This problem *is* discussed in several other threads in this and other forums.  So far, I have found no one with a solution.

The error is "no address associated with hostname", which, if that really is the problem, means it's likely a DNS error.  I seem to recall a U.S. Supreme Court ruling about a month ago that said ISPs could de-prioritize or block certain high-volume traffic, such as youtube.  Is it possible that ISPs are choosing to block the Ubuntu servers by simply omitting the association between the domain and the IP?  If so, I have to agree with the description, "something wicked has happened".

I'm suspicious of that last one because I switched ISPs about the same time this issue cropped up for me.

---

### Post by ryan858 on 2010-05-16
You might try adding your Sources to /etc/resolv.conf

You can read up on resolv.conf if you don't know how it works...

---

### Post by newb85 on 2010-05-16
Thank you for pointing me in the right direction.  For some reason, the Belkin wireless router I had just switched to was offering itself as a DNS server.  Because the only lines set up in my resolv.conf were for the router, I copy-pasted a line someone else had posted [here]("http://www.debianhelp.org/node/8521") and commented out the lines for the router.  Presto! Problem solved.

I'm really curious, though, as to what exactly I've done by manually entering 208.180.42.68.  Is that the DNS for a random ISP?  Would it speed things up if I contacted my local ISP for their DNS server IP?  Are such DNS servers usually on a static IP?

Also, the resolv.conf file said it was generated by NetworkManager.  Will NetworkManager overwrite my settings if I connect to another network?

---

### Post by ryan858 on 2010-05-16
> **newb85 said:**
> Thank you for pointing me in the right direction.  For some reason, the Belkin wireless router I had just switched to was offering itself as a DNS server.  Because the only lines set up in my resolv.conf were for the router, I copy-pasted a line someone else had posted [here]("http://www.debianhelp.org/node/8521") and commented out the lines for the router.  Presto! Problem solved.

I'm really curious, though, as to what exactly I've done by manually entering 208.180.42.68.  Is that the DNS for a random ISP?  Would it speed things up if I contacted my local ISP for their DNS server IP?  Are such DNS servers usually on a static IP?

Also, the resolv.conf file said it was generated by NetworkManager.  Will NetworkManager overwrite my settings if I connect to another network?

It sounds like it wasn't registering from a valid DNS server. Your router should act as a DNS server itself, since it can resolve addresses through the ISP's DNS server given to it by the DHCP. So you should really only need the address of your router in resolv.conf.

You should have something like: 
nameserver 192.168.1.1

or whatever your router's address is.

I don't know if anything is updated when you move to another network, and if not then that would be the problem. The resolv.conf would have the wrong address, and if its setup for static IP, not DHCP, then a few other things will be incorrect as well.

You should have the network setup as Automatic (DHCP) and add the correct nameserver to resolv.conf


You can also use a free DNS server, such as OpenDNS. Here are some free DNS's:
[http://theos.in/windows-xp/free-fast-public-dns-server-list/](http://theos.in/windows-xp/free-fast-public-dns-server-list/)

Google's 8.8.8.8 seems to be the fastest one for me... I'd say use that one.

Using a 3rd party DNS you can go from network to network, and not have to change resolv.conf

Also: you do not need anything in resolv.conf except for *nameserver <address>*
unless you want to have it search for addresses in a specific domain, such as a local network, then you would add:
[I]search <domain>
[/I]For example:[I] search blah.org
[/I]

---

### Post by newb85 on 2010-05-17
> It sounds like it wasn't registering from a valid DNS server. Your  router should act as a DNS server itself, since it can resolve addresses  through the ISP's DNS server given to it by the DHCP. So you should  really only need the address of your router in resolv.conf.

When the computer was restarted, NetworkManager did in fact overwrite my settings and set up the router as the DNS server again, which once again caused problems downloading the indexes for updates.  I believe this reverted because I *did* have the network set up as *Automatic DHCP*.  I'm switched it to *Automatic DHCP addresses only* and manually entered 8.8.8.8 as the DNS server.  That fixed the index download issue so that it should stay fixed when reconnecting to the network.

In short, the issue is that the router does an unsatisfactory job resolving addresses, and the simplest solution I've found is to set up NetworkManager client-side to always use a third-party DNS, such as Google (8.8.8.8), when connecting to that network, instead of using the router.

---

### Post by somakd on 2010-10-12
I faced the same problem...

You must have installed google-chat etc... here's what solved the problemo

I removed google's name from the repository list 
and 
also the key installed by google from the authentication list
(go to synaptic -> repository   and you will find these items/tabs)

then apt-get update works like good-old-days :popcorn:

random note: Google's getting too much powerful :-k

---

