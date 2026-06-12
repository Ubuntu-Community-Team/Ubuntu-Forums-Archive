---
title: "cant install updates on 11.04"
date: 2012-02-04
forum: General Help
---

### Post by tim_norman2003 on 2012-02-04
i tried installing updates and it wont work for some reason..
as far as i know this is completely random. 
the attached screenshot shows the message which comes up after i type my password when trying to update the 20 or so required updates, some of them 'important security' updates.. 

please help
Tim

---

### Post by CatKiller on 2012-02-04
I'd wager you've added repositories to your sources.list without adding the cryptographic key used to sign that repository. Remove the entries or add the key (the place you got the entry from will tell you how) and your problem will go away.

---

### Post by shakabra on 2012-02-04
Could you try ```
sudo apt-get update && sudo apt-get upgrade
``` from the terminal. If it doesn't work please post the output.

---

### Post by tim_norman2003 on 2012-02-04
(thinking about it, i think it happened after tryingto install medibuntu, ive checked synaptic package manager, to get rid of medibuntu stuff, but nothing comes up if i search for it...)

> **shakabra said:**
> Could you try ```
sudo apt-get update && sudo apt-get upgrade
``` from the terminal. If it doesn't work please post the output.


i ran that, it didnt work unfortunately. this is what is said in terminal:

tim@tim-desktop:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for tim: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty InRelease                               
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates InRelease                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty Release.gpg                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates Release.gpg                     
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease [7,093 B]                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty Release                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates Release                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main i386 Packages                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free i386 Packages/DiffIndex           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted i386 Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe i386 Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse i386 Packages                
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe TranslationIndex               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main i386 Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted i386 Packages        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe i386 Packages          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse i386 Packages        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free i386 Packages/DiffIndex       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Translation-en_GB                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Translation-en_GB            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Translation-en_GB              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free TranslationIndex                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free TranslationIndex              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_GB           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free i386 Packages                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_GB       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free i386 Packages                 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Translation-en                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Translation-en               
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Translation-en               
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Translation-en                 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Translation-en_GB          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Translation-en             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Translation-en_GB    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Translation-en       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Translation-en_GB    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Translation-en       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Translation-en_GB      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Translation-en         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_GB                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Ign [http://le-web.org](http://le-web.org) stable InRelease                                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_GB                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Ign [http://le-web.org](http://le-web.org) stable Release.gpg                                       
Ign [http://le-web.org](http://le-web.org) stable Release                                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en_GB                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Translation-en_GB             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Translation-en                
Ign [http://le-web.org](http://le-web.org) stable/main TranslationIndex                             
Err [http://le-web.org](http://le-web.org) stable/main i386 Packages                                
  404  Not Found
Ign [http://le-web.org](http://le-web.org) stable/main Translation-en_GB
Ign [http://le-web.org](http://le-web.org) stable/main Translation-en   
Fetched 1 B in 27s (0 B/s)
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch [http://le-web.org/repository/dists/stable/main/binary-i386/Packages](http://le-web.org/repository/dists/stable/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by shakabra on 2012-02-04
Yup CatKiller called it do this
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0C5A2783
```
This will add the GPG key.

---

### Post by tim_norman2003 on 2012-02-04
> **shakabra said:**
> Yup CatKiller called it do this
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0C5A2783
```
This will add the GPG key.

that didnt work. got the same message :/

---

