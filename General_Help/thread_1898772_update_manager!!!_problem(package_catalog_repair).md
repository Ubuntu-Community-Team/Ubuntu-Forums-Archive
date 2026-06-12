---
title: "update manager!!! problem(package catalog repair)"
date: 2011-12-22
forum: General Help
---

### Post by arun_nr on 2011-12-22
heii friends


i recently upgraded to ubuntu 11.10 and was working fine until the update manager had some problem!!
when i look for updates it now shows a message that packet manager needs to have a "package catalog repair"and updates are not working from then.when i gave the password for upgrade it says failure occured!!
i hav a gud internet connection and still hav a problem troublshooting wat is d problem?:popcorn:




pls help:confused:

---

### Post by shakabra on 2011-12-22
Take a look in your sources.list. You probably still have some old references to the previous version in there.

---

### Post by plucky on 2011-12-22
> **arun_nr said:**
> heii friends


i recently upgraded to ubuntu 11.10 and was working fine until the update manager had some problem!!
when i look for updates it now shows a message that packet manager needs to have a "package catalog repair"and updates are not working from then.when i gave the password for upgrade it says failure occured!!
i hav a gud internet connection and still hav a problem troublshooting wat is d problem?:popcorn:




pls help:confused:


Post the full output from a terminal for ```
sudo apt-get update
```

---

### Post by arun_nr on 2011-12-22
this is the output


Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Get:1 [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg [198 B]                 
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]                        
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg [198 B]          
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg [198 B]                 
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]                     
Get:6 [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg [198 B]                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                        
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg [198 B]         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources/DiffIndex                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources/DiffIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release                               
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release [9,752 B]                       
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
  
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages/DiffIndex                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources/DiffIndex   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources/DiffIndex     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources/DiffIndex   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages/DiffIndex   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages/DiffIndex
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release [32.4 kB]           
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release                       
  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages/DiffIndex       
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages/DiffIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources             
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources/DiffIndex               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources/DiffIndex                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources/DiffIndex          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources/DiffIndex            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources/DiffIndex          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages/DiffIndex          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages/DiffIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex 
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en     
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                    
  404  Not Found
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US            
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages              
  404  Not Found
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
Fetched 1,380 B in 6s (204 B/s)                                                
Reading package lists... Done
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C2518248EEA14886

W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: Failed to fetch [http://ppa.launchpad.net/webupd8team/gnome3/ubuntu/dists/oneiric/Release](http://ppa.launchpad.net/webupd8team/gnome3/ubuntu/dists/oneiric/Release)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release)  

W: Failed to fetch [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by plucky on 2011-12-22
> Take a look in your sources.list. You probably still have some old references to the previous version in there. 

Remove all references to "natty" and the PPA's that is giving you the 404 errors and see if you still get the same problem.


Good Luck

---

### Post by arun_nr on 2012-01-01
happy newyear


it didnt work out!!!


i got some other op


Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Get:2 [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg [198 B]                 
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg [198 B]                 
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg [198 B]          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]                     
Get:6 [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg [198 B]                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                        
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg [198 B]         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources/DiffIndex                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources/DiffIndex         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release                               
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release [9,752 B]                       
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
  
Ign [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages/DiffIndex                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release [32.4 kB]           
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release                       
  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources/DiffIndex   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources/DiffIndex     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources/DiffIndex   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages/DiffIndex   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages/DiffIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages/DiffIndex       
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources/DiffIndex                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources/DiffIndex          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources/DiffIndex            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources/DiffIndex          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages/DiffIndex          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages/DiffIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources             
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources/DiffIndex               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages/DiffIndex    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages/DiffIndex      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages/DiffIndex    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en     
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources               
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                    
  404  Not Found
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
  404  Not Found
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
Fetched 1,380 B in 8s (162 B/s)                                                
Reading package lists... Done
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C2518248EEA14886

W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: Failed to fetch [http://ppa.launchpad.net/webupd8team/gnome3/ubuntu/dists/oneiric/Release](http://ppa.launchpad.net/webupd8team/gnome3/ubuntu/dists/oneiric/Release)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release)  

W: Failed to fetch [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by plucky on 2012-01-01
Post output for ```
cat /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list
```

Also try a different server.

Good Luck

---

### Post by yugnip on 2012-01-01
Yes, get rid of the Natty repos, they are still present. Bisigi Themes are no longer for 11.10 I believe (could be mistaken) so that could be the reason for the 404 there. Remove that ppa as well.

The gpg errors can be fixed manually or by using Y PPA manager, which I just did a post on here: [http://ubuntuforums.org/showpost.php?p=11579254&postcount=5](http://ubuntuforums.org/showpost.php?p=11579254&postcount=5)

---

### Post by arun_nr on 2012-01-01
i guess for more clarity i will put the source file here!!



# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.

---

### Post by plucky on 2012-01-01
> ## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
**deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner**

Put a # in front of that line

What about the other command?

```
cat /etc/apt/sources.list.d/*.list
```

---

### Post by arun_nr on 2012-01-01
ya output for dat one!!


~$ cat /etc/apt/sources.list.d/*.list
deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) oneiric main
deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) oneiric main
# deb [http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu](http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu) oneiric main # disabled on upgrade to oneiric
# deb-src [http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu](http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu) oneiric main # disabled on upgrade to oneiric
# deb [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu) oneiric main # disabled on upgrade to oneiric
# deb-src [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu) oneiric main # disabled on upgrade to oneiric
deb [http://ppa.launchpad.net/webupd8team/gnome3/ubuntu](http://ppa.launchpad.net/webupd8team/gnome3/ubuntu) oneiric main
deb-src [http://ppa.launchpad.net/webupd8team/gnome3/ubuntu](http://ppa.launchpad.net/webupd8team/gnome3/ubuntu) oneiric main
deb [http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu](http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu) oneiric main
deb-src [http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu](http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu) oneiric main

---

### Post by arun_nr on 2012-01-01
:p

---

### Post by yugnip on 2012-01-01
Add a # to the Bisigi repo and that will eliminate the 404 errors. Next try Y PPA Manager ( I see it installed in your sources list) and click the 'advanced' button. There is an option there to fix gpg key errors. Try that and then update. Hopefully problems solved.

---

### Post by arun_nr on 2012-01-01
i didnt find any repo of bisgi in my sourcefile?

---

### Post by oldos2er on 2012-01-01
Check /etc/apt/sources.list.d/ for any bisigi* files, and move or delete them.

---

### Post by yugnip on 2012-01-01
> **arun_nr said:**
> 


~$ cat /etc/apt/sources.list.d/*.list
[B]deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) oneiric main
deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) oneiric main[/B]
# deb [http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu](http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu) oneiric main # disabled on upgrade to oneiric
# deb-src [http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu](http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu) oneiric main # disabled on upgrade to oneiric
# deb [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu) oneiric main # disabled on upgrade to oneiric
# deb-src [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu) oneiric main # disabled on upgrade to oneiric
deb [http://ppa.launchpad.net/webupd8team/gnome3/ubuntu](http://ppa.launchpad.net/webupd8team/gnome3/ubuntu) oneiric main
deb-src [http://ppa.launchpad.net/webupd8team/gnome3/ubuntu](http://ppa.launchpad.net/webupd8team/gnome3/ubuntu) oneiric main
deb [http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu](http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu) oneiric main
deb-src [http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu](http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu) oneiric main

The first two in bold are Bisigi. Place a # in from of them.

---

### Post by arun_nr on 2012-01-06
now  when i did that and rtied again for update
i got fail to download packages messages and in details: these things needed to be installed.
libmikmod2 libportmidi0 libsdl-mixer1.2 libsdl-ttf2.0-0 libsmpeg0 monsterz monsterz-data python-pygame

the former one was for a game.

and dis one for arduino 
ca-certificates-java default-jre default-jre-headless java-common  libaccess-bridge-java libaccess-bridge-java-jni libjna-java libnss3-1d  librxtx-java ttf-dejavu-extra
  do u know how to install these stuffs?

---

