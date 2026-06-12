---
title: "Updating issues..."
date: 2012-03-05
forum: General Help
---

### Post by Panxo on 2012-03-05
Hi there.

I'm using ubuntu 11.10. I was trying to run again Vbox, but it failed due to updates not done. 

I thought that a sudo apt-get update will work, but then here's what I've got:

```
Ign http://download.virtualbox.org oneiric InRelease
Ign http://security.ubuntu.com oneiric-security InRelease                      
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://extras.ubuntu.com oneiric InRelease                                 
Hit http://download.virtualbox.org oneiric Release.gpg                         
Hit http://download.virtualbox.org oneiric Release                             
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://security.ubuntu.com oneiric-security Release.gpg                    
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Hit http://download.virtualbox.org oneiric/contrib amd64 Packages              
Hit http://security.ubuntu.com oneiric-security Release                        
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://download.virtualbox.org oneiric/contrib i386 Packages               
Ign http://download.virtualbox.org oneiric/contrib TranslationIndex            
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://security.ubuntu.com oneiric-security/main Sources                   
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://security.ubuntu.com oneiric-security/restricted Sources             
Hit http://security.ubuntu.com oneiric-security/universe Sources               
Hit http://security.ubuntu.com oneiric-security/multiverse Sources             
Hit http://security.ubuntu.com oneiric-security/main amd64 Packages            
Hit http://security.ubuntu.com oneiric-security/restricted amd64 Packages      
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                       
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://security.ubuntu.com oneiric-security/universe amd64 Packages        
Hit http://security.ubuntu.com oneiric-security/multiverse amd64 Packages      
Hit http://security.ubuntu.com oneiric-security/main i386 Packages             
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages       
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages         
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages       
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex          
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex      
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://security.ubuntu.com oneiric-security/main Translation-en            
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://security.ubuntu.com oneiric-security/universe Translation-en        
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Ign http://download.virtualbox.org oneiric/contrib Translation-en_US           
Ign http://download.virtualbox.org oneiric/contrib Translation-en              
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                    
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Err http://cl.archive.ubuntu.com oneiric InRelease                             
  
Err http://cl.archive.ubuntu.com oneiric-updates InRelease
  
Err http://cl.archive.ubuntu.com oneiric-backports InRelease
  
Err http://cl.archive.ubuntu.com oneiric Release.gpg     
  Unable to connect to cl.archive.ubuntu.com:http:
Err http://cl.archive.ubuntu.com oneiric-updates Release.gpg
  Unable to connect to cl.archive.ubuntu.com:http:
Err http://cl.archive.ubuntu.com oneiric-backports Release.gpg
  Unable to connect to cl.archive.ubuntu.com:http:
Reading package lists... Done
W: Failed to fetch http://cl.archive.ubuntu.com/ubuntu/dists/oneiric/InRelease  

W: Failed to fetch http://cl.archive.ubuntu.com/ubuntu/dists/oneiric-updates/InRelease  

W: Failed to fetch http://cl.archive.ubuntu.com/ubuntu/dists/oneiric-backports/InRelease  

W: Failed to fetch http://cl.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg  Unable to connect to cl.archive.ubuntu.com:http:

W: Failed to fetch http://cl.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg  Unable to connect to cl.archive.ubuntu.com:http:

W: Failed to fetch http://cl.archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release.gpg  Unable to connect to cl.archive.ubuntu.com:http:

W: Some index files failed to download. They have been ignored, or old ones used instead.
```Lately I've been trying to run NVIDIA drivers, and it crashes with OpenLG. Cairo-dock stop working until I log out and log in again using cairo-dock... I think that something went wrong there, but I don't know what. I tried reinstalling Nvidia, and OpenLG many times, but nothing is working. In fact, last time Vbox stop working and now I can't even do a simple update from the terminal. 

I did also try reinstalling Vbox but it still doesn't run any session...

---

### Post by lechien73 on 2012-03-05
The [http://cl.archive.ubuntu.com/](http://cl.archive.ubuntu.com/) repository is offline, so try using a different repository.

Go to **Software Center**, choose the **Edit** menu and go to **Software Sources**

Set your download location to the main server, and try that.

---

### Post by Panxo on 2012-03-05
Alright... I could go into the software source that you said, but I don't have any idea about doing what you said. Could you tell me where and how I have to do that? Please.

---

### Post by MG&amp;TL on 2012-03-05
Just change the "server for" entry to "Main server" -screen shot attached.

---

### Post by Panxo on 2012-03-06
Great! Thanks you both. 

I got less errors than last time.

After the update here's what I've got:

```
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric InRelease
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric Release.gpg
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Release
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric Release
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/main TranslationIndex
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/restricted TranslationIndex
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Translation-en
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/main amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/restricted amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/main Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/main Translation-en
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/restricted Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/restricted Translation-en
Ign http://download.virtualbox.org oneiric InRelease                           
Ign http://extras.ubuntu.com oneiric InRelease                                 
Hit http://download.virtualbox.org oneiric Release.gpg                         
Hit http://download.virtualbox.org oneiric Release                             
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://archive.canonical.com oneiric InRelease                             
Get:1 http://extras.ubuntu.com oneiric Release.gpg [72 B]                      
Ign http://us.archive.ubuntu.com oneiric InRelease                             
Ign http://us.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://us.archive.ubuntu.com oneiric-backports InRelease                   
Hit http://download.virtualbox.org oneiric/contrib amd64 Packages              
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://archive.canonical.com oneiric Release.gpg                           
Hit http://download.virtualbox.org oneiric/contrib i386 Packages               
Ign http://us.archive.ubuntu.com oneiric-security InRelease                    
Get:2 http://us.archive.ubuntu.com oneiric Release.gpg [198 B]                 
Get:3 http://us.archive.ubuntu.com oneiric-updates Release.gpg [198 B]         
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://archive.canonical.com oneiric Release                               
Hit http://extras.ubuntu.com oneiric/main Sources                              
Ign http://download.virtualbox.org oneiric/contrib TranslationIndex            
Get:4 http://us.archive.ubuntu.com oneiric-backports Release.gpg [198 B]       
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                       
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Hit http://archive.canonical.com oneiric/partner Sources                       
Get:5 http://us.archive.ubuntu.com oneiric-security Release.gpg [198 B]        
Get:6 http://us.archive.ubuntu.com oneiric Release [40.8 kB]                   
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Get:7 http://us.archive.ubuntu.com oneiric-updates Release [40.8 kB]           
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Get:8 http://us.archive.ubuntu.com oneiric-backports Release [40.8 kB]         
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Get:9 http://us.archive.ubuntu.com oneiric-security Release [40.8 kB]          
Ign http://download.virtualbox.org oneiric/contrib Translation-en_US           
Get:10 http://us.archive.ubuntu.com oneiric/main Sources [877 kB]              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Ign http://download.virtualbox.org oneiric/contrib Translation-en              
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                    
Ign http://archive.canonical.com oneiric/partner Translation-en_US             
Ign http://extras.ubuntu.com oneiric/main Translation-en                      
Ign http://archive.canonical.com oneiric/partner Translation-en               
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                   
Ign http://ppa.launchpad.net oneiric/main Translation-en
Get:11 http://us.archive.ubuntu.com oneiric/restricted Sources [5,351 B]
Get:12 http://us.archive.ubuntu.com oneiric/multiverse Sources [149 kB]
Get:13 http://us.archive.ubuntu.com oneiric/universe Sources [4,677 kB]        
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Get:14 http://us.archive.ubuntu.com oneiric/main amd64 Packages [1,226 kB]                                                                 
Get:15 http://us.archive.ubuntu.com oneiric/restricted amd64 Packages [8,261 B]                                                            
Get:16 http://us.archive.ubuntu.com oneiric/universe amd64 Packages [4,460 kB]                                                             
Get:17 http://us.archive.ubuntu.com oneiric/multiverse amd64 Packages [117 kB]                                                             
Get:18 http://us.archive.ubuntu.com oneiric/main i386 Packages [1,226 kB]                                                                  
Get:19 http://us.archive.ubuntu.com oneiric/restricted i386 Packages [8,216 B]                                                             
Get:20 http://us.archive.ubuntu.com oneiric/universe i386 Packages [4,468 kB]                                                              
Get:21 http://us.archive.ubuntu.com oneiric/multiverse i386 Packages [119 kB]                                                              
Get:22 http://us.archive.ubuntu.com oneiric/main TranslationIndex [3,289 B]                                                                
Get:23 http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex [2,265 B]                                                          
Get:24 http://us.archive.ubuntu.com oneiric/restricted TranslationIndex [2,263 B]                                                          
Get:25 http://us.archive.ubuntu.com oneiric/universe TranslationIndex [2,640 B]                                                            
Get:26 http://us.archive.ubuntu.com oneiric-updates/restricted Sources [1,337 B]                                                           
Get:27 http://us.archive.ubuntu.com oneiric-updates/main Sources [127 kB]                                                                  
Get:28 http://us.archive.ubuntu.com oneiric-updates/multiverse Sources [3,648 B]                                                           
Get:29 http://us.archive.ubuntu.com oneiric-updates/universe Sources [45.7 kB]                                                             
Get:30 http://us.archive.ubuntu.com oneiric-updates/main amd64 Packages [292 kB]                                                           
Get:31 http://us.archive.ubuntu.com oneiric-updates/restricted amd64 Packages [2,982 B]                                                    
Get:32 http://us.archive.ubuntu.com oneiric-updates/universe amd64 Packages [99.5 kB]                                                      
Get:33 http://us.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages [6,202 B]                                                    
Get:34 http://us.archive.ubuntu.com oneiric-updates/main i386 Packages [293 kB]                                                            
Get:35 http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages [2,968 B]                                                     
Get:36 http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages [99.9 kB]                                                       
Get:37 http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages [6,359 B]                                                     
Get:38 http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex [74 B]                                                           
Get:39 http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [72 B]                                                     
Get:40 http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex [71 B]                                                     
Get:41 http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex [73 B]                                                       
Get:42 http://us.archive.ubuntu.com oneiric-backports/main Sources [2,207 B]                                                               
Get:43 http://us.archive.ubuntu.com oneiric-backports/restricted Sources [14 B]                                                            
Get:44 http://us.archive.ubuntu.com oneiric-backports/universe Sources [6,563 B]                                                           
Get:45 http://us.archive.ubuntu.com oneiric-backports/multiverse Sources [14 B]                                                            
Get:46 http://us.archive.ubuntu.com oneiric-backports/main amd64 Packages [2,807 B]                                                        
Get:47 http://us.archive.ubuntu.com oneiric-backports/restricted amd64 Packages [14 B]                                                     
Get:48 http://us.archive.ubuntu.com oneiric-backports/universe amd64 Packages [7,631 B]                                                    
Get:49 http://us.archive.ubuntu.com oneiric-backports/multiverse amd64 Packages [14 B]                                                     
Get:50 http://us.archive.ubuntu.com oneiric-backports/main i386 Packages [2,819 B]                                                         
Get:51 http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages [14 B]                                                      
Get:52 http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages [7,643 B]                                                     
Get:53 http://us.archive.ubuntu.com oneiric-backports/multiverse i386 Packages [14 B]                                                      
Get:54 http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex [72 B]                                                         
Get:55 http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex [70 B]                                                   
Get:56 http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex [70 B]                                                   
Get:57 http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex [72 B]                                                     
Get:58 http://us.archive.ubuntu.com oneiric-security/restricted Sources [14 B]                                                             
Get:59 http://us.archive.ubuntu.com oneiric-security/main Sources [31.8 kB]                                                                
Get:60 http://us.archive.ubuntu.com oneiric-security/multiverse Sources [1,654 B]                                                          
Get:61 http://us.archive.ubuntu.com oneiric-security/universe Sources [11.4 kB]                                                            
Get:62 http://us.archive.ubuntu.com oneiric-security/main amd64 Packages [84.4 kB]                                                         
Get:63 http://us.archive.ubuntu.com oneiric-security/restricted amd64 Packages [14 B]                                                      
Get:64 http://us.archive.ubuntu.com oneiric-security/universe amd64 Packages [29.1 kB]                                                     
Get:65 http://us.archive.ubuntu.com oneiric-security/multiverse amd64 Packages [3,194 B]                                                   
Get:66 http://us.archive.ubuntu.com oneiric-security/main i386 Packages [84.6 kB]                                                          
Get:67 http://us.archive.ubuntu.com oneiric-security/restricted i386 Packages [14 B]                                                       
Get:68 http://us.archive.ubuntu.com oneiric-security/universe i386 Packages [29.1 kB]                                                      
Get:69 http://us.archive.ubuntu.com oneiric-security/multiverse i386 Packages [3,362 B]                                                    
Get:70 http://us.archive.ubuntu.com oneiric-security/main TranslationIndex [73 B]                                                          
Get:71 http://us.archive.ubuntu.com oneiric-security/multiverse TranslationIndex [72 B]                                                    
Get:72 http://us.archive.ubuntu.com oneiric-security/restricted TranslationIndex [70 B]                                                    
Get:73 http://us.archive.ubuntu.com oneiric-security/universe TranslationIndex [73 B]                                                      
Get:74 http://us.archive.ubuntu.com oneiric/main Translation-en [701 kB]                                                                   
Get:75 http://us.archive.ubuntu.com oneiric/multiverse Translation-en [92.6 kB]                                                            
Get:76 http://us.archive.ubuntu.com oneiric/restricted Translation-en [2,229 B]                                                            
Get:77 http://us.archive.ubuntu.com oneiric/universe Translation-en [3,165 kB]                                                             
Get:78 http://us.archive.ubuntu.com oneiric-updates/main Translation-en [137 kB]                                                           
Get:79 http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en [3,524 B]                                                    
Get:80 http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en [508 B]                                                      
Get:81 http://us.archive.ubuntu.com oneiric-updates/universe Translation-en [60.0 kB]                                                      
Get:82 http://us.archive.ubuntu.com oneiric-backports/main Translation-en [1,712 B]                                                        
Get:83 http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en [14 B]                                                     
Get:84 http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en [14 B]                                                     
Get:85 http://us.archive.ubuntu.com oneiric-backports/universe Translation-en [5,979 B]                                                    
Get:86 http://us.archive.ubuntu.com oneiric-security/main Translation-en [47.2 kB]                                                         
Get:87 http://us.archive.ubuntu.com oneiric-security/multiverse Translation-en [1,494 B]                                                   
Get:88 http://us.archive.ubuntu.com oneiric-security/restricted Translation-en [14 B]                                                      
Get:89 http://us.archive.ubuntu.com oneiric-security/universe Translation-en [20.3 kB]                                                     
Fetched 23.0 MB in 35s (642 kB/s)                                                                                                          
W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Does anyone know how to fix 'em?

---

### Post by Script Warlock on 2012-03-06
> **Panxo said:**
> Great! Thanks you both. 

I got less errors than last time.

After the update here's what I've got:

```
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric InRelease
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric Release.gpg
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Release
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric Release
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/main TranslationIndex
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/restricted TranslationIndex
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Translation-en
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/main amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/restricted amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/main Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/main Translation-en
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/restricted Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/restricted Translation-en
Ign http://download.virtualbox.org oneiric InRelease                           
Ign http://extras.ubuntu.com oneiric InRelease                                 
Hit http://download.virtualbox.org oneiric Release.gpg                         
Hit http://download.virtualbox.org oneiric Release                             
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://archive.canonical.com oneiric InRelease                             
Get:1 http://extras.ubuntu.com oneiric Release.gpg [72 B]                      
Ign http://us.archive.ubuntu.com oneiric InRelease                             
Ign http://us.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://us.archive.ubuntu.com oneiric-backports InRelease                   
Hit http://download.virtualbox.org oneiric/contrib amd64 Packages              
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://archive.canonical.com oneiric Release.gpg                           
Hit http://download.virtualbox.org oneiric/contrib i386 Packages               
Ign http://us.archive.ubuntu.com oneiric-security InRelease                    
Get:2 http://us.archive.ubuntu.com oneiric Release.gpg [198 B]                 
Get:3 http://us.archive.ubuntu.com oneiric-updates Release.gpg [198 B]         
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://archive.canonical.com oneiric Release                               
Hit http://extras.ubuntu.com oneiric/main Sources                              
Ign http://download.virtualbox.org oneiric/contrib TranslationIndex            
Get:4 http://us.archive.ubuntu.com oneiric-backports Release.gpg [198 B]       
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                       
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Hit http://archive.canonical.com oneiric/partner Sources                       
Get:5 http://us.archive.ubuntu.com oneiric-security Release.gpg [198 B]        
Get:6 http://us.archive.ubuntu.com oneiric Release [40.8 kB]                   
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Get:7 http://us.archive.ubuntu.com oneiric-updates Release [40.8 kB]           
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Get:8 http://us.archive.ubuntu.com oneiric-backports Release [40.8 kB]         
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Get:9 http://us.archive.ubuntu.com oneiric-security Release [40.8 kB]          
Ign http://download.virtualbox.org oneiric/contrib Translation-en_US           
Get:10 http://us.archive.ubuntu.com oneiric/main Sources [877 kB]              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Ign http://download.virtualbox.org oneiric/contrib Translation-en              
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                    
Ign http://archive.canonical.com oneiric/partner Translation-en_US             
Ign http://extras.ubuntu.com oneiric/main Translation-en                      
Ign http://archive.canonical.com oneiric/partner Translation-en               
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                   
Ign http://ppa.launchpad.net oneiric/main Translation-en
Get:11 http://us.archive.ubuntu.com oneiric/restricted Sources [5,351 B]
Get:12 http://us.archive.ubuntu.com oneiric/multiverse Sources [149 kB]
Get:13 http://us.archive.ubuntu.com oneiric/universe Sources [4,677 kB]        
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Get:14 http://us.archive.ubuntu.com oneiric/main amd64 Packages [1,226 kB]                                                                 
Get:15 http://us.archive.ubuntu.com oneiric/restricted amd64 Packages [8,261 B]                                                            
Get:16 http://us.archive.ubuntu.com oneiric/universe amd64 Packages [4,460 kB]                                                             
Get:17 http://us.archive.ubuntu.com oneiric/multiverse amd64 Packages [117 kB]                                                             
Get:18 http://us.archive.ubuntu.com oneiric/main i386 Packages [1,226 kB]                                                                  
Get:19 http://us.archive.ubuntu.com oneiric/restricted i386 Packages [8,216 B]                                                             
Get:20 http://us.archive.ubuntu.com oneiric/universe i386 Packages [4,468 kB]                                                              
Get:21 http://us.archive.ubuntu.com oneiric/multiverse i386 Packages [119 kB]                                                              
Get:22 http://us.archive.ubuntu.com oneiric/main TranslationIndex [3,289 B]                                                                
Get:23 http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex [2,265 B]                                                          
Get:24 http://us.archive.ubuntu.com oneiric/restricted TranslationIndex [2,263 B]                                                          
Get:25 http://us.archive.ubuntu.com oneiric/universe TranslationIndex [2,640 B]                                                            
Get:26 http://us.archive.ubuntu.com oneiric-updates/restricted Sources [1,337 B]                                                           
Get:27 http://us.archive.ubuntu.com oneiric-updates/main Sources [127 kB]                                                                  
Get:28 http://us.archive.ubuntu.com oneiric-updates/multiverse Sources [3,648 B]                                                           
Get:29 http://us.archive.ubuntu.com oneiric-updates/universe Sources [45.7 kB]                                                             
Get:30 http://us.archive.ubuntu.com oneiric-updates/main amd64 Packages [292 kB]                                                           
Get:31 http://us.archive.ubuntu.com oneiric-updates/restricted amd64 Packages [2,982 B]                                                    
Get:32 http://us.archive.ubuntu.com oneiric-updates/universe amd64 Packages [99.5 kB]                                                      
Get:33 http://us.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages [6,202 B]                                                    
Get:34 http://us.archive.ubuntu.com oneiric-updates/main i386 Packages [293 kB]                                                            
Get:35 http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages [2,968 B]                                                     
Get:36 http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages [99.9 kB]                                                       
Get:37 http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages [6,359 B]                                                     
Get:38 http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex [74 B]                                                           
Get:39 http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [72 B]                                                     
Get:40 http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex [71 B]                                                     
Get:41 http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex [73 B]                                                       
Get:42 http://us.archive.ubuntu.com oneiric-backports/main Sources [2,207 B]                                                               
Get:43 http://us.archive.ubuntu.com oneiric-backports/restricted Sources [14 B]                                                            
Get:44 http://us.archive.ubuntu.com oneiric-backports/universe Sources [6,563 B]                                                           
Get:45 http://us.archive.ubuntu.com oneiric-backports/multiverse Sources [14 B]                                                            
Get:46 http://us.archive.ubuntu.com oneiric-backports/main amd64 Packages [2,807 B]                                                        
Get:47 http://us.archive.ubuntu.com oneiric-backports/restricted amd64 Packages [14 B]                                                     
Get:48 http://us.archive.ubuntu.com oneiric-backports/universe amd64 Packages [7,631 B]                                                    
Get:49 http://us.archive.ubuntu.com oneiric-backports/multiverse amd64 Packages [14 B]                                                     
Get:50 http://us.archive.ubuntu.com oneiric-backports/main i386 Packages [2,819 B]                                                         
Get:51 http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages [14 B]                                                      
Get:52 http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages [7,643 B]                                                     
Get:53 http://us.archive.ubuntu.com oneiric-backports/multiverse i386 Packages [14 B]                                                      
Get:54 http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex [72 B]                                                         
Get:55 http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex [70 B]                                                   
Get:56 http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex [70 B]                                                   
Get:57 http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex [72 B]                                                     
Get:58 http://us.archive.ubuntu.com oneiric-security/restricted Sources [14 B]                                                             
Get:59 http://us.archive.ubuntu.com oneiric-security/main Sources [31.8 kB]                                                                
Get:60 http://us.archive.ubuntu.com oneiric-security/multiverse Sources [1,654 B]                                                          
Get:61 http://us.archive.ubuntu.com oneiric-security/universe Sources [11.4 kB]                                                            
Get:62 http://us.archive.ubuntu.com oneiric-security/main amd64 Packages [84.4 kB]                                                         
Get:63 http://us.archive.ubuntu.com oneiric-security/restricted amd64 Packages [14 B]                                                      
Get:64 http://us.archive.ubuntu.com oneiric-security/universe amd64 Packages [29.1 kB]                                                     
Get:65 http://us.archive.ubuntu.com oneiric-security/multiverse amd64 Packages [3,194 B]                                                   
Get:66 http://us.archive.ubuntu.com oneiric-security/main i386 Packages [84.6 kB]                                                          
Get:67 http://us.archive.ubuntu.com oneiric-security/restricted i386 Packages [14 B]                                                       
Get:68 http://us.archive.ubuntu.com oneiric-security/universe i386 Packages [29.1 kB]                                                      
Get:69 http://us.archive.ubuntu.com oneiric-security/multiverse i386 Packages [3,362 B]                                                    
Get:70 http://us.archive.ubuntu.com oneiric-security/main TranslationIndex [73 B]                                                          
Get:71 http://us.archive.ubuntu.com oneiric-security/multiverse TranslationIndex [72 B]                                                    
Get:72 http://us.archive.ubuntu.com oneiric-security/restricted TranslationIndex [70 B]                                                    
Get:73 http://us.archive.ubuntu.com oneiric-security/universe TranslationIndex [73 B]                                                      
Get:74 http://us.archive.ubuntu.com oneiric/main Translation-en [701 kB]                                                                   
Get:75 http://us.archive.ubuntu.com oneiric/multiverse Translation-en [92.6 kB]                                                            
Get:76 http://us.archive.ubuntu.com oneiric/restricted Translation-en [2,229 B]                                                            
Get:77 http://us.archive.ubuntu.com oneiric/universe Translation-en [3,165 kB]                                                             
Get:78 http://us.archive.ubuntu.com oneiric-updates/main Translation-en [137 kB]                                                           
Get:79 http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en [3,524 B]                                                    
Get:80 http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en [508 B]                                                      
Get:81 http://us.archive.ubuntu.com oneiric-updates/universe Translation-en [60.0 kB]                                                      
Get:82 http://us.archive.ubuntu.com oneiric-backports/main Translation-en [1,712 B]                                                        
Get:83 http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en [14 B]                                                     
Get:84 http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en [14 B]                                                     
Get:85 http://us.archive.ubuntu.com oneiric-backports/universe Translation-en [5,979 B]                                                    
Get:86 http://us.archive.ubuntu.com oneiric-security/main Translation-en [47.2 kB]                                                         
Get:87 http://us.archive.ubuntu.com oneiric-security/multiverse Translation-en [1,494 B]                                                   
Get:88 http://us.archive.ubuntu.com oneiric-security/restricted Translation-en [14 B]                                                      
Get:89 http://us.archive.ubuntu.com oneiric-security/universe Translation-en [20.3 kB]                                                     
Fetched 23.0 MB in 35s (642 kB/s)                                                                                                          
W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Does anyone know how to fix 'em? > Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/main amd64 Packages is the cdrom unchecked on the software sources?

---

### Post by Panxo on 2012-03-06
Yup, now it's! And one error less for update.

Here's what I've got now:

```
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric InRelease
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric Release.gpg
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Release
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric Release
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/main TranslationIndex
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/restricted TranslationIndex
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Translation-en
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/main amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/restricted amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/main Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/main Translation-en
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/restricted Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric/restricted Translation-en
Ign http://download.virtualbox.org oneiric InRelease                           
Ign http://extras.ubuntu.com oneiric InRelease                                 
Hit http://download.virtualbox.org oneiric Release.gpg                         
Hit http://download.virtualbox.org oneiric Release                             
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://archive.canonical.com oneiric InRelease                             
Get:1 http://extras.ubuntu.com oneiric Release.gpg [72 B]                      
Ign http://us.archive.ubuntu.com oneiric InRelease                             
Ign http://us.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://us.archive.ubuntu.com oneiric-backports InRelease                   
Hit http://download.virtualbox.org oneiric/contrib amd64 Packages              
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://archive.canonical.com oneiric Release.gpg                           
Hit http://download.virtualbox.org oneiric/contrib i386 Packages               
Ign http://us.archive.ubuntu.com oneiric-security InRelease                    
Get:2 http://us.archive.ubuntu.com oneiric Release.gpg [198 B]                 
Get:3 http://us.archive.ubuntu.com oneiric-updates Release.gpg [198 B]         
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://archive.canonical.com oneiric Release                               
Hit http://extras.ubuntu.com oneiric/main Sources                              
Ign http://download.virtualbox.org oneiric/contrib TranslationIndex            
Get:4 http://us.archive.ubuntu.com oneiric-backports Release.gpg [198 B]       
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                       
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Hit http://archive.canonical.com oneiric/partner Sources                       
Get:5 http://us.archive.ubuntu.com oneiric-security Release.gpg [198 B]        
Get:6 http://us.archive.ubuntu.com oneiric Release [40.8 kB]                   
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Get:7 http://us.archive.ubuntu.com oneiric-updates Release [40.8 kB]           
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Get:8 http://us.archive.ubuntu.com oneiric-backports Release [40.8 kB]         
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Get:9 http://us.archive.ubuntu.com oneiric-security Release [40.8 kB]          
Ign http://download.virtualbox.org oneiric/contrib Translation-en_US           
Get:10 http://us.archive.ubuntu.com oneiric/main Sources [877 kB]              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Ign http://download.virtualbox.org oneiric/contrib Translation-en              
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                    
Ign http://archive.canonical.com oneiric/partner Translation-en_US             
Ign http://extras.ubuntu.com oneiric/main Translation-en                      
Ign http://archive.canonical.com oneiric/partner Translation-en               
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                   
Ign http://ppa.launchpad.net oneiric/main Translation-en
Get:11 http://us.archive.ubuntu.com oneiric/restricted Sources [5,351 B]
Get:12 http://us.archive.ubuntu.com oneiric/multiverse Sources [149 kB]
Get:13 http://us.archive.ubuntu.com oneiric/universe Sources [4,677 kB]        
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Get:14 http://us.archive.ubuntu.com oneiric/main amd64 Packages [1,226 kB]                                                                 
Get:15 http://us.archive.ubuntu.com oneiric/restricted amd64 Packages [8,261 B]                                                            
Get:16 http://us.archive.ubuntu.com oneiric/universe amd64 Packages [4,460 kB]                                                             
Get:17 http://us.archive.ubuntu.com oneiric/multiverse amd64 Packages [117 kB]                                                             
Get:18 http://us.archive.ubuntu.com oneiric/main i386 Packages [1,226 kB]                                                                  
Get:19 http://us.archive.ubuntu.com oneiric/restricted i386 Packages [8,216 B]                                                             
Get:20 http://us.archive.ubuntu.com oneiric/universe i386 Packages [4,468 kB]                                                              
Get:21 http://us.archive.ubuntu.com oneiric/multiverse i386 Packages [119 kB]                                                              
Get:22 http://us.archive.ubuntu.com oneiric/main TranslationIndex [3,289 B]                                                                
Get:23 http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex [2,265 B]                                                          
Get:24 http://us.archive.ubuntu.com oneiric/restricted TranslationIndex [2,263 B]                                                          
Get:25 http://us.archive.ubuntu.com oneiric/universe TranslationIndex [2,640 B]                                                            
Get:26 http://us.archive.ubuntu.com oneiric-updates/restricted Sources [1,337 B]                                                           
Get:27 http://us.archive.ubuntu.com oneiric-updates/main Sources [127 kB]                                                                  
Get:28 http://us.archive.ubuntu.com oneiric-updates/multiverse Sources [3,648 B]                                                           
Get:29 http://us.archive.ubuntu.com oneiric-updates/universe Sources [45.7 kB]                                                             
Get:30 http://us.archive.ubuntu.com oneiric-updates/main amd64 Packages [292 kB]                                                           
Get:31 http://us.archive.ubuntu.com oneiric-updates/restricted amd64 Packages [2,982 B]                                                    
Get:32 http://us.archive.ubuntu.com oneiric-updates/universe amd64 Packages [99.5 kB]                                                      
Get:33 http://us.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages [6,202 B]                                                    
Get:34 http://us.archive.ubuntu.com oneiric-updates/main i386 Packages [293 kB]                                                            
Get:35 http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages [2,968 B]                                                     
Get:36 http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages [99.9 kB]                                                       
Get:37 http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages [6,359 B]                                                     
Get:38 http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex [74 B]                                                           
Get:39 http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [72 B]                                                     
Get:40 http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex [71 B]                                                     
Get:41 http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex [73 B]                                                       
Get:42 http://us.archive.ubuntu.com oneiric-backports/main Sources [2,207 B]                                                               
Get:43 http://us.archive.ubuntu.com oneiric-backports/restricted Sources [14 B]                                                            
Get:44 http://us.archive.ubuntu.com oneiric-backports/universe Sources [6,563 B]                                                           
Get:45 http://us.archive.ubuntu.com oneiric-backports/multiverse Sources [14 B]                                                            
Get:46 http://us.archive.ubuntu.com oneiric-backports/main amd64 Packages [2,807 B]                                                        
Get:47 http://us.archive.ubuntu.com oneiric-backports/restricted amd64 Packages [14 B]                                                     
Get:48 http://us.archive.ubuntu.com oneiric-backports/universe amd64 Packages [7,631 B]                                                    
Get:49 http://us.archive.ubuntu.com oneiric-backports/multiverse amd64 Packages [14 B]                                                     
Get:50 http://us.archive.ubuntu.com oneiric-backports/main i386 Packages [2,819 B]                                                         
Get:51 http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages [14 B]                                                      
Get:52 http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages [7,643 B]                                                     
Get:53 http://us.archive.ubuntu.com oneiric-backports/multiverse i386 Packages [14 B]                                                      
Get:54 http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex [72 B]                                                         
Get:55 http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex [70 B]                                                   
Get:56 http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex [70 B]                                                   
Get:57 http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex [72 B]                                                     
Get:58 http://us.archive.ubuntu.com oneiric-security/restricted Sources [14 B]                                                             
Get:59 http://us.archive.ubuntu.com oneiric-security/main Sources [31.8 kB]                                                                
Get:60 http://us.archive.ubuntu.com oneiric-security/multiverse Sources [1,654 B]                                                          
Get:61 http://us.archive.ubuntu.com oneiric-security/universe Sources [11.4 kB]                                                            
Get:62 http://us.archive.ubuntu.com oneiric-security/main amd64 Packages [84.4 kB]                                                         
Get:63 http://us.archive.ubuntu.com oneiric-security/restricted amd64 Packages [14 B]                                                      
Get:64 http://us.archive.ubuntu.com oneiric-security/universe amd64 Packages [29.1 kB]                                                     
Get:65 http://us.archive.ubuntu.com oneiric-security/multiverse amd64 Packages [3,194 B]                                                   
Get:66 http://us.archive.ubuntu.com oneiric-security/main i386 Packages [84.6 kB]                                                          
Get:67 http://us.archive.ubuntu.com oneiric-security/restricted i386 Packages [14 B]                                                       
Get:68 http://us.archive.ubuntu.com oneiric-security/universe i386 Packages [29.1 kB]                                                      
Get:69 http://us.archive.ubuntu.com oneiric-security/multiverse i386 Packages [3,362 B]                                                    
Get:70 http://us.archive.ubuntu.com oneiric-security/main TranslationIndex [73 B]                                                          
Get:71 http://us.archive.ubuntu.com oneiric-security/multiverse TranslationIndex [72 B]                                                    
Get:72 http://us.archive.ubuntu.com oneiric-security/restricted TranslationIndex [70 B]                                                    
Get:73 http://us.archive.ubuntu.com oneiric-security/universe TranslationIndex [73 B]                                                      
Get:74 http://us.archive.ubuntu.com oneiric/main Translation-en [701 kB]                                                                   
Get:75 http://us.archive.ubuntu.com oneiric/multiverse Translation-en [92.6 kB]                                                            
Get:76 http://us.archive.ubuntu.com oneiric/restricted Translation-en [2,229 B]                                                            
Get:77 http://us.archive.ubuntu.com oneiric/universe Translation-en [3,165 kB]                                                             
Get:78 http://us.archive.ubuntu.com oneiric-updates/main Translation-en [137 kB]                                                           
Get:79 http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en [3,524 B]                                                    
Get:80 http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en [508 B]                                                      
Get:81 http://us.archive.ubuntu.com oneiric-updates/universe Translation-en [60.0 kB]                                                      
Get:82 http://us.archive.ubuntu.com oneiric-backports/main Translation-en [1,712 B]                                                        
Get:83 http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en [14 B]                                                     
Get:84 http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en [14 B]                                                     
Get:85 http://us.archive.ubuntu.com oneiric-backports/universe Translation-en [5,979 B]                                                    
Get:86 http://us.archive.ubuntu.com oneiric-security/main Translation-en [47.2 kB]                                                         
Get:87 http://us.archive.ubuntu.com oneiric-security/multiverse Translation-en [1,494 B]                                                   
Get:88 http://us.archive.ubuntu.com oneiric-security/restricted Translation-en [14 B]                                                      
Get:89 http://us.archive.ubuntu.com oneiric-security/universe Translation-en [20.3 kB]                                                     
Fetched 23.0 MB in 35s (642 kB/s)                                                                                                          
W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
pango@Panxo:~$ clear

pango@Panxo:~$ sudo apt-get update
sudo: unable to resolve host Panxo
[sudo] password for pango: 
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Release.gpg                           
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Release                               
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Packages                              
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Translation-en_US                     
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Translation-en                        
Ign http://download.virtualbox.org oneiric InRelease                                                                                       
Ign http://ppa.launchpad.net oneiric InRelease                                                                                             
Ign http://ppa.launchpad.net oneiric InRelease                                                                                             
Ign http://ppa.launchpad.net oneiric InRelease                                                                             
Ign http://archive.canonical.com oneiric InRelease                                                                                         
Hit http://download.virtualbox.org oneiric Release.gpg                                                                                     
Ign http://extras.ubuntu.com oneiric InRelease                                                                             
Hit http://download.virtualbox.org oneiric Release                                                                         
Ign http://ppa.launchpad.net oneiric InRelease                                                                    
Hit http://ppa.launchpad.net oneiric Release.gpg                                           
Hit http://ppa.launchpad.net oneiric Release.gpg                                           
Hit http://archive.canonical.com oneiric Release.gpg                                                             
Ign http://us.archive.ubuntu.com oneiric InRelease                                                               
Ign http://us.archive.ubuntu.com oneiric-updates InRelease                                 
Ign http://us.archive.ubuntu.com oneiric-backports InRelease                                                     
Hit http://download.virtualbox.org oneiric/contrib amd64 Packages                                                
Hit http://extras.ubuntu.com oneiric Release.gpg                                           
Hit http://ppa.launchpad.net oneiric Release.gpg                                           
Hit http://archive.canonical.com oneiric Release                                           
Hit http://download.virtualbox.org oneiric/contrib i386 Packages                                                  
Ign http://us.archive.ubuntu.com oneiric-security InRelease                                                      
Hit http://us.archive.ubuntu.com oneiric Release.gpg                                                             
Hit http://extras.ubuntu.com oneiric Release                                                                     
Hit http://ppa.launchpad.net oneiric Release.gpg                                                                  
Hit http://ppa.launchpad.net oneiric Release                                                                     
Hit http://archive.canonical.com oneiric/partner Sources                                                                                
Ign http://download.virtualbox.org oneiric/contrib TranslationIndex                                              
Hit http://us.archive.ubuntu.com oneiric-updates Release.gpg                               
Hit http://us.archive.ubuntu.com oneiric-backports Release.gpg                                                   
Hit http://extras.ubuntu.com oneiric/main Sources                                                                
Hit http://ppa.launchpad.net oneiric Release                                                                     
Hit http://archive.canonical.com oneiric/partner amd64 Packages                                                                         
Hit http://archive.canonical.com oneiric/partner i386 Packages                                                   
Hit http://us.archive.ubuntu.com oneiric-security Release.gpg                                                    
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                                                         
Hit http://extras.ubuntu.com oneiric/main i386 Packages                                    
Hit http://ppa.launchpad.net oneiric Release                                                                     
Hit http://ppa.launchpad.net oneiric Release                                                                     
Ign http://archive.canonical.com oneiric/partner TranslationIndex                                                                       
Hit http://us.archive.ubuntu.com oneiric Release                                                                 
Hit http://us.archive.ubuntu.com oneiric-updates Release                                                         
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                                                                              
Hit http://ppa.launchpad.net oneiric/main Sources                                                                
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                                   
Hit http://ppa.launchpad.net oneiric/main i386 Packages                                    
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                 
Hit http://us.archive.ubuntu.com oneiric-backports Release                                                       
Hit http://ppa.launchpad.net oneiric/main Sources                                                                                       
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                                                         
Hit http://ppa.launchpad.net oneiric/main i386 Packages                                                          
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                                       
Hit http://ppa.launchpad.net oneiric/main Sources                                                                
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                                   
Hit http://ppa.launchpad.net oneiric/main i386 Packages                                    
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                 
Hit http://ppa.launchpad.net oneiric/main Sources                                          
Hit http://us.archive.ubuntu.com oneiric-security Release                                                        
Hit http://us.archive.ubuntu.com oneiric/main Sources                                                                                   
Hit http://us.archive.ubuntu.com oneiric/restricted Sources                                                                             
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources                                                                             
Hit http://us.archive.ubuntu.com oneiric/universe Sources                                                                               
Hit http://us.archive.ubuntu.com oneiric/main amd64 Packages                                                                            
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                                                                                
Hit http://ppa.launchpad.net oneiric/main i386 Packages                                                          
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                                       
Hit http://us.archive.ubuntu.com oneiric/restricted amd64 Packages                         
Hit http://us.archive.ubuntu.com oneiric/universe amd64 Packages                                                 
Hit http://us.archive.ubuntu.com oneiric/multiverse amd64 Packages                                               
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages                                                      
Hit http://us.archive.ubuntu.com oneiric/restricted i386 Packages                                                
Hit http://us.archive.ubuntu.com oneiric/universe i386 Packages                                                  
Hit http://us.archive.ubuntu.com oneiric/multiverse i386 Packages                          
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex                             
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex                       
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex                                             
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex                                               
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Sources                                              
Hit http://us.archive.ubuntu.com oneiric-updates/main Sources                                                    
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Sources                                              
Hit http://us.archive.ubuntu.com oneiric-updates/universe Sources                                                
Ign http://download.virtualbox.org oneiric/contrib Translation-en_US                                             
Ign http://download.virtualbox.org oneiric/contrib Translation-en                                                
Hit http://us.archive.ubuntu.com oneiric-updates/main amd64 Packages                       
Hit http://us.archive.ubuntu.com oneiric-updates/restricted amd64 Packages                 
Hit http://us.archive.ubuntu.com oneiric-updates/universe amd64 Packages                   
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages                 
Hit http://us.archive.ubuntu.com oneiric-updates/main i386 Packages                        
Hit http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages                  
Hit http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages                    
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages                  
Hit http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex                     
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex               
Hit http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex               
Hit http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex                 
Hit http://us.archive.ubuntu.com oneiric-backports/main Sources                            
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Sources                      
Hit http://us.archive.ubuntu.com oneiric-backports/universe Sources                        
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Sources                      
Hit http://us.archive.ubuntu.com oneiric-backports/main amd64 Packages                     
Hit http://us.archive.ubuntu.com oneiric-backports/restricted amd64 Packages               
Hit http://us.archive.ubuntu.com oneiric-backports/universe amd64 Packages                 
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse amd64 Packages               
Hit http://us.archive.ubuntu.com oneiric-backports/main i386 Packages                      
Hit http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages                
Hit http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages                  
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse i386 Packages                
Hit http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex                   
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex             
Hit http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex             
Hit http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-security/restricted Sources 
Hit http://us.archive.ubuntu.com oneiric-security/main Sources       
Ign http://archive.canonical.com oneiric/partner Translation-en_US                         
Hit http://us.archive.ubuntu.com oneiric-security/multiverse Sources                       
Hit http://us.archive.ubuntu.com oneiric-security/universe Sources                         
Hit http://us.archive.ubuntu.com oneiric-security/main amd64 Packages                      
Hit http://us.archive.ubuntu.com oneiric-security/restricted amd64 Packages                
Hit http://us.archive.ubuntu.com oneiric-security/universe amd64 Packages                  
Hit http://us.archive.ubuntu.com oneiric-security/multiverse amd64 Packages                
Hit http://us.archive.ubuntu.com oneiric-security/main i386 Packages                       
Hit http://us.archive.ubuntu.com oneiric-security/restricted i386 Packages                 
Hit http://us.archive.ubuntu.com oneiric-security/universe i386 Packages                   
Ign http://extras.ubuntu.com oneiric/main Translation-en_US          
Ign http://archive.canonical.com oneiric/partner Translation-en      
Hit http://us.archive.ubuntu.com oneiric-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric-security/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-security/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/main Translation-en         
Ign http://extras.ubuntu.com oneiric/main Translation-en             
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en   
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/universe Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Ign http://ppa.launchpad.net oneiric/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Hit http://us.archive.ubuntu.com oneiric-backports/universe Translation-en
Hit http://us.archive.ubuntu.com oneiric-security/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-security/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-security/universe Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en
W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Last thing is what I think it's not allowing me to run any session on Vbox 'cause it also says something about the upgrades; they weren't fully completed or something alike.

---

### Post by lechien73 on 2012-03-06
Ok, I think there could still be some problem with your software sources.

Could you post the contents of your /etc/apt/sources.list file here between [CODE] tags, please?

Also, when you say that Virtualbox won't let you start any session - does the Virtualbox console start up at all? Or do you just get the error when trying to start a VM?

---

### Post by mörgæs on 2012-03-06
If everything else fails, you can generate a new sources.list. There is a link to it in my signature.

---

### Post by raja.genupula on 2012-03-06
hi this one also useful to generate new source list in easy way
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by Panxo on 2012-03-06
> **lechien73 said:**
> Ok, I think there could still be some problem with your software sources.

Could you post the contents of your /etc/apt/sources.list file here between [CODE] tags, please?

Also, when you say that Virtualbox won't let you start any session - does the Virtualbox console start up at all? Or do you just get the error when trying to start a VM?


How do I get the contents? Just writing that down on a terminal?

And, yes, it starts up just as normal, but when I tell it to start win 7 it tells me that about the update and go back to normal as long as I don't try to start win 7 again.

---

### Post by plucky on 2012-03-06
> How do I get the contents? Just writing that down on a terminal?



Open a terminal and post output for ```
cat /etc/apt/sources.list
```

---

### Post by Panxo on 2012-03-06
Alright, thanks.

Here it's:

```
deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted #Added by software-properties

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse #Added by software-properties

deb http://us.archive.ubuntu.com/ubuntu/ oneiric-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-security restricted main multiverse universe #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-security universe
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
deb http://ppa.launchpad.net/s-elser/winelol/ubuntu NATTY main
deb-src http://ppa.launchpad.net/s-elser/winelol/ubuntu NATTY main

```

---

### Post by plucky on 2012-03-06
Edit the file with ```
gksudo gedit /etc/apt/sources.list
``` and put a # in front of ```
deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/
deb http://ppa.launchpad.net/s-elser/winelol/ubuntu NATTY main
deb-src http://ppa.launchpad.net/s-elser/winelol/ubuntu NATTY main
```

and all the lines that begin with **deb-src** as you don't need the sources code repositories.

So the file looks like ```
#deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted #Added by software-properties

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse #Added by software-properties

deb http://us.archive.ubuntu.com/ubuntu/ oneiric-security main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-security restricted main multiverse universe #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-security universe
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
#deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
#deb-src http://extras.ubuntu.com/ubuntu oneiric main
#deb http://ppa.launchpad.net/s-elser/winelol/ubuntu NATTY main
#deb-src http://ppa.launchpad.net/s-elser/winelol/ubuntu NATTY main
```

Good Luck

---

### Post by Panxo on 2012-03-07
Great thanks everyone! 

No errors nor warnings this time, everything seems to be working perfectly. Well, except for Vbox which is still not starting any session due to the same problem.

---

### Post by lechien73 on 2012-03-07
Glad the updating issue is solved. Could I suggest that you use the **Thread Tools** menu above the posts to mark this as [SOLVED], and then create a new thread for your Virtualbox problem?

It would be handy to know exactly what errors you're getting when trying to launch Virtualbox sessions - with screenshots if possible :)

---

### Post by Panxo on 2012-03-07
No problem, I'll do that. Thanks again!

---

