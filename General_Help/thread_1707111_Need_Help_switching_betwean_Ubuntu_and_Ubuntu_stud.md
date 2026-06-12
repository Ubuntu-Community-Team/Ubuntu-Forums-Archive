---
title: "Need Help switching betwean Ubuntu and Ubuntu studio"
date: 2011-03-14
forum: General Help
---

### Post by Reduced_Oxygen on 2011-03-14
Hi, I want to change from ubuntu 11.04 to ubuntu studio. Is there any way to do this without losing all my stuff/with out completely reinstalling the os?

---

### Post by Reduced_Oxygen on 2011-03-14
NM found it
```
 do aptitude update && sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt 
```
 
[https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu]("https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu")

---

### Post by Reduced_Oxygen on 2011-03-15
Ok so i tryed that code and i get this error:
```
 sudo aptitude update && sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
[sudo] password for gilligan: 
sudo: aptitude: command not found

```

---

### Post by Reduced_Oxygen on 2011-03-15
ok i have found what appears to be the solution

```
 sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graph

```

---

### Post by Reduced_Oxygen on 2011-03-15
this appeared to work but there are no evident changes

```
 gilligan@Gilligan-desktop:~$  sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graph
[sudo] password for gilligan: 
Ign http://mirror.netspace.net.au natty InRelease
Ign http://mirror.netspace.net.au natty-updates InRelease                      
Ign http://mirror.netspace.net.au natty-backports InRelease                    
Ign http://mirror.netspace.net.au natty-security InRelease                     
Ign http://mirror.netspace.net.au natty-proposed InRelease                     
Get:1 http://mirror.netspace.net.au natty Release.gpg [198 B]                  
Hit http://mirror.netspace.net.au natty-updates Release.gpg                    
Hit http://mirror.netspace.net.au natty-backports Release.gpg                  
Hit http://mirror.netspace.net.au natty-security Release.gpg                   
Hit http://mirror.netspace.net.au natty-proposed Release.gpg                   
Get:2 http://mirror.netspace.net.au natty Release [39.8 kB]                    
Hit http://mirror.netspace.net.au natty-updates Release                        
Hit http://mirror.netspace.net.au natty-backports Release                      
Hit http://mirror.netspace.net.au natty-security Release                       
Hit http://mirror.netspace.net.au natty-proposed Release                       
Get:3 http://mirror.netspace.net.au natty/main Sources [864 kB]                
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                 
Ign http://archive.canonical.com natty InRelease                             
Ign http://extras.ubuntu.com natty InRelease                                 
Ign http://ppa.launchpad.net natty Release.gpg                               
Hit http://archive.canonical.com natty Release.gpg                             
Hit http://extras.ubuntu.com natty Release.gpg                                 
Get:4 http://ppa.launchpad.net natty Release.gpg [316 B]                       
Get:5 http://mirror.netspace.net.au natty/restricted Sources [4,095 B]         
Hit http://archive.canonical.com natty Release                                 
Get:6 http://mirror.netspace.net.au natty/multiverse Sources [155 kB]          
Get:7 http://mirror.netspace.net.au natty/universe Sources [4,407 kB]          
Hit http://extras.ubuntu.com natty Release                                     
Ign http://ppa.launchpad.net natty Release.gpg                                 
Hit http://archive.canonical.com natty/partner Sources                         
Ign http://ppa.launchpad.net natty Release                                    
Hit http://extras.ubuntu.com natty/main Sources                                
Hit http://archive.canonical.com natty/partner i386 Packages                   
Ign http://archive.canonical.com natty/partner TranslationIndex                
Get:8 http://ppa.launchpad.net natty Release [9,747 B]                         
Hit http://extras.ubuntu.com natty/main i386 Packages                          
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Ign http://ppa.launchpad.net natty Release                                     
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Get:9 http://ppa.launchpad.net natty/main Sources [14 B]                       
Get:10 http://ppa.launchpad.net natty/main i386 Packages [668 B]               
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Get:11 http://mirror.netspace.net.au natty/main i386 Packages [1,570 kB]       
Ign http://archive.canonical.com natty/partner Translation-en_US               
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://extras.ubuntu.com natty/main Translation-en                         
Err http://ppa.launchpad.net natty/main Sources                                
  404  Not Found
Err http://ppa.launchpad.net natty/main i386 Packages                          
  404  Not Found
Err http://ppa.launchpad.net natty/main Sources                                
  404  Not Found
Get:12 http://mirror.netspace.net.au natty/restricted i386 Packages [9,027 B]  
Get:13 http://mirror.netspace.net.au natty/universe i386 Packages [6,046 kB]   
Err http://ppa.launchpad.net natty/main i386 Packages                          
  404  Not Found
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Get:14 http://mirror.netspace.net.au natty/multiverse i386 Packages [184 kB]   
Ign http://mirror.netspace.net.au natty/main TranslationIndex                  
Ign http://mirror.netspace.net.au natty/multiverse TranslationIndex            
Ign http://mirror.netspace.net.au natty/restricted TranslationIndex            
Ign http://mirror.netspace.net.au natty/universe TranslationIndex              
Hit http://mirror.netspace.net.au natty-updates/restricted Sources             
Hit http://mirror.netspace.net.au natty-updates/main Sources                   
Hit http://mirror.netspace.net.au natty-updates/multiverse Sources             
Hit http://mirror.netspace.net.au natty-updates/universe Sources               
Hit http://mirror.netspace.net.au natty-updates/main i386 Packages             
Hit http://mirror.netspace.net.au natty-updates/restricted i386 Packages       
Hit http://mirror.netspace.net.au natty-updates/universe i386 Packages         
Hit http://mirror.netspace.net.au natty-updates/multiverse i386 Packages       
Ign http://mirror.netspace.net.au natty-updates/main TranslationIndex          
Ign http://mirror.netspace.net.au natty-updates/multiverse TranslationIndex    
Ign http://mirror.netspace.net.au natty-updates/restricted TranslationIndex    
Ign http://mirror.netspace.net.au natty-updates/universe TranslationIndex      
Hit http://mirror.netspace.net.au natty-backports/main Sources                 
Hit http://mirror.netspace.net.au natty-backports/restricted Sources           
Hit http://mirror.netspace.net.au natty-backports/universe Sources             
Hit http://mirror.netspace.net.au natty-backports/multiverse Sources           
Hit http://mirror.netspace.net.au natty-backports/main i386 Packages           
Hit http://mirror.netspace.net.au natty-backports/restricted i386 Packages     
Hit http://mirror.netspace.net.au natty-backports/universe i386 Packages       
Hit http://mirror.netspace.net.au natty-backports/multiverse i386 Packages     
Ign http://mirror.netspace.net.au natty-backports/main TranslationIndex        
Ign http://mirror.netspace.net.au natty-backports/multiverse TranslationIndex  
Ign http://mirror.netspace.net.au natty-backports/restricted TranslationIndex  
Ign http://mirror.netspace.net.au natty-backports/universe TranslationIndex    
Hit http://mirror.netspace.net.au natty-security/restricted Sources            
Hit http://mirror.netspace.net.au natty-security/main Sources                  
Hit http://mirror.netspace.net.au natty-security/multiverse Sources            
Hit http://mirror.netspace.net.au natty-security/universe Sources              
Hit http://mirror.netspace.net.au natty-security/main i386 Packages            
Hit http://mirror.netspace.net.au natty-security/restricted i386 Packages      
Hit http://mirror.netspace.net.au natty-security/universe i386 Packages        
Hit http://mirror.netspace.net.au natty-security/multiverse i386 Packages      
Ign http://mirror.netspace.net.au natty-security/main TranslationIndex         
Ign http://mirror.netspace.net.au natty-security/multiverse TranslationIndex   
Ign http://mirror.netspace.net.au natty-security/restricted TranslationIndex   
Ign http://mirror.netspace.net.au natty-security/universe TranslationIndex     
Hit http://mirror.netspace.net.au natty-proposed/restricted Sources            
Hit http://mirror.netspace.net.au natty-proposed/main Sources                  
Hit http://mirror.netspace.net.au natty-proposed/multiverse Sources            
Hit http://mirror.netspace.net.au natty-proposed/universe Sources              
Hit http://mirror.netspace.net.au natty-proposed/restricted i386 Packages      
Hit http://mirror.netspace.net.au natty-proposed/main i386 Packages            
Hit http://mirror.netspace.net.au natty-proposed/multiverse i386 Packages      
Hit http://mirror.netspace.net.au natty-proposed/universe i386 Packages        
Ign http://mirror.netspace.net.au natty-proposed/main TranslationIndex         
Ign http://mirror.netspace.net.au natty-proposed/multiverse TranslationIndex   
Ign http://mirror.netspace.net.au natty-proposed/restricted TranslationIndex   
Ign http://mirror.netspace.net.au natty-proposed/universe TranslationIndex     
Ign http://mirror.netspace.net.au natty/main Translation-en_US                 
Ign http://mirror.netspace.net.au natty/main Translation-en                    
Ign http://mirror.netspace.net.au natty/multiverse Translation-en_US           
Ign http://mirror.netspace.net.au natty/multiverse Translation-en              
Ign http://mirror.netspace.net.au natty/restricted Translation-en_US           
Ign http://mirror.netspace.net.au natty/restricted Translation-en              
Ign http://mirror.netspace.net.au natty/universe Translation-en_US             
Ign http://mirror.netspace.net.au natty/universe Translation-en                
Ign http://mirror.netspace.net.au natty-updates/main Translation-en_US         
Ign http://mirror.netspace.net.au natty-updates/main Translation-en            
Ign http://mirror.netspace.net.au natty-updates/multiverse Translation-en_US   
Ign http://mirror.netspace.net.au natty-updates/multiverse Translation-en      
Ign http://mirror.netspace.net.au natty-updates/restricted Translation-en_US   
Ign http://mirror.netspace.net.au natty-updates/restricted Translation-en      
Ign http://mirror.netspace.net.au natty-updates/universe Translation-en_US     
Ign http://mirror.netspace.net.au natty-updates/universe Translation-en        
Ign http://mirror.netspace.net.au natty-backports/main Translation-en_US       
Ign http://mirror.netspace.net.au natty-backports/main Translation-en          
Ign http://mirror.netspace.net.au natty-backports/multiverse Translation-en_US 
Ign http://mirror.netspace.net.au natty-backports/multiverse Translation-en    
Ign http://mirror.netspace.net.au natty-backports/restricted Translation-en_US 
Ign http://mirror.netspace.net.au natty-backports/restricted Translation-en    
Ign http://mirror.netspace.net.au natty-backports/universe Translation-en_US   
Ign http://mirror.netspace.net.au natty-backports/universe Translation-en      
Ign http://mirror.netspace.net.au natty-security/main Translation-en_US        
Ign http://mirror.netspace.net.au natty-security/main Translation-en           
Ign http://mirror.netspace.net.au natty-security/multiverse Translation-en_US  
Ign http://mirror.netspace.net.au natty-security/multiverse Translation-en     
Ign http://mirror.netspace.net.au natty-security/restricted Translation-en_US  
Ign http://mirror.netspace.net.au natty-security/restricted Translation-en     
Ign http://mirror.netspace.net.au natty-security/universe Translation-en_US    
Ign http://mirror.netspace.net.au natty-security/universe Translation-en       
Ign http://mirror.netspace.net.au natty-proposed/main Translation-en_US        
Ign http://mirror.netspace.net.au natty-proposed/main Translation-en           
Ign http://mirror.netspace.net.au natty-proposed/multiverse Translation-en_US  
Ign http://mirror.netspace.net.au natty-proposed/multiverse Translation-en     
Ign http://mirror.netspace.net.au natty-proposed/restricted Translation-en_US  
Ign http://mirror.netspace.net.au natty-proposed/restricted Translation-en     
Ign http://mirror.netspace.net.au natty-proposed/universe Translation-en_US    
Ign http://mirror.netspace.net.au natty-proposed/universe Translation-en       
Fetched 13.3 MB in 15s (863 kB/s)                                              
W: Failed to fetch http://ppa.launchpad.net/gregory-hainaut/pcsx2.official.ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/gregory-hainaut/pcsx2.official.ppa/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead. 
```

---

### Post by leg on 2011-03-15
Well you have got some failed updates near the end of your output but I am not sure where ubuntu-studio is. I don't think it is in any ppa and possibly in multiverse or something. You won't notice any changes to the desktop when you update this way but you should check the applications menu and see if the applications have been installed. Also the ubuntu-studio theme(s) will be available to you if you also installed those. The main one to check is the audio menu as there would be a lot of apps in there if you have indeed installed studio.

the [package list]("https://wiki.ubuntu.com/UbuntuStudio/PackageList") you can check that they are installed..

---

### Post by Reduced_Oxygen on 2011-03-15
doing it that way nothing changed, i'm currently trying to install everything through synaptic package manager

---

### Post by Reduced_Oxygen on 2011-03-15
appears to have worked

---

