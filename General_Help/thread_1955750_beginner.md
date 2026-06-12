---
title: "beginner"
date: 2012-04-10
forum: General Help
---

### Post by ramanathan on 2012-04-10
i try to install the goggle talk in my ubuntu 11.10 os but i can't.so i cancel it and try to update my os there is a error message so i use the command nautilus and delete the password.dat file.After that there is a error message shown below during update.................

```
ramanathan@ramanathan:~$ sudo apt-get update
[sudo] password for ramanathan: 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric InRelease                             
Err [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                               
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                    
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates InRelease                     
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric Release.gpg                           
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages/DiffIndex       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources/DiffIndex                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources/DiffIndex         
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates Release.gpg                   
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric Release                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources/DiffIndex   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources/DiffIndex     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates Release                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources/DiffIndex   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/main Sources/DiffIndex                
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/restricted Sources/DiffIndex          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages/DiffIndex   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/universe Sources/DiffIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/multiverse Sources/DiffIndex          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/main i386 Packages/DiffIndex          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/restricted i386 Packages/DiffIndex    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/universe i386 Packages/DiffIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/multiverse i386 Packages/DiffIndex    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/main TranslationIndex                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex      
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Err [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Err [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US             
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/universe TranslationIndex             
Err [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/main Sources/DiffIndex        
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/restricted Sources/DiffIndex  
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/universe Sources/DiffIndex    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/multiverse Sources/DiffIndex  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/main i386 Packages/DiffIndex  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                      
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/restricted i386 Packages/DiffIndex
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US                  
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/universe i386 Packages/DiffIndex
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/main TranslationIndex       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/universe TranslationIndex   
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                 
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources           
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources             
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources           
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages     
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en_US       
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en          
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en_US 
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en_US   
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en      
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/main Sources                        
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/restricted Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/universe Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/multiverse Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/main i386 Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/restricted i386 Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/universe i386 Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/multiverse i386 Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/main Translation-en_US
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/main Translation-en
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/multiverse Translation-en_US
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/multiverse Translation-en
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/restricted Translation-en_US
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/restricted Translation-en
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/universe Translation-en_US
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/universe Translation-en
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/main Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/restricted Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/universe Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/multiverse Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/main i386 Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/restricted i386 Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/universe i386 Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/main Translation-en_US
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/main Translation-en
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/multiverse Translation-en_US
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/multiverse Translation-en
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/restricted Translation-en_US
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/restricted Translation-en
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/universe Translation-en_US
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/universe Translation-en
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/Release.gpg](http://archive.canonical.com/ubuntu/dists/oneiric/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/partner/binary-i386/Packages](http://archive.canonical.com/ubuntu/dists/oneiric/partner/binary-i386/Packages)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/source/Sources)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/partner/i18n/Translation-en_US](http://archive.canonical.com/ubuntu/dists/oneiric/partner/i18n/Translation-en_US)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/partner/i18n/Translation-en](http://archive.canonical.com/ubuntu/dists/oneiric/partner/i18n/Translation-en)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/source/Sources)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en_US](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en_US)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/source/Sources)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/source/Sources)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/source/Sources)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/binary-i386/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/universe/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/universe/source/Sources)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/binary-i386/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/source/Sources)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/binary-i386/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/binary-i386/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/i18n/Translation-en_US](http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/i18n/Translation-en_US)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/i18n/Translation-en)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/i18n/Translation-en_US](http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/i18n/Translation-en_US)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/i18n/Translation-en)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/i18n/Translation-en_US](http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/i18n/Translation-en_US)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/i18n/Translation-en)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en_US](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en_US)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/i18n/Translation-en_US](http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/i18n/Translation-en_US)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/i18n/Translation-en)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Translation-en_US](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Translation-en_US)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Translation-en_US](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Translation-en_US)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Translation-en_US](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Translation-en_US)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/source/Sources)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/source/Sources)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/source/Sources)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/source/Sources)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Translation-en_US](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Translation-en_US)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/i18n/Translation-en_US](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/i18n/Translation-en_US)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/i18n/Translation-en_US](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/i18n/Translation-en_US)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/i18n/Translation-en_US](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/i18n/Translation-en_US)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.
ramanathan@ramanathan:~$
```

---

### Post by riderplus on 2012-04-10
> **ramanathan said:**
> so i use the command nautilus and delete the password.dat file.

Why in the world would you do that?? Don't fix anything if it ain't broken.

---

