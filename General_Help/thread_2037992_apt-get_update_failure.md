---
title: "apt-get update failure"
date: 2012-08-05
forum: General Help
---

### Post by Moeller on 2012-08-05
I did the said sudo apt - get update , and this is what I get it. very frustrating. I am realativly new so any help and breaking it down barney style would be much appreciated. that you.

```
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/restricted/binary-i386/ InRelease
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/main/binary-i386/ Release
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/restricted/binary-i386/ Release
Err cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/main/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/main/binary-i386/ Translation-en
Err cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/restricted/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/restricted/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/restricted/binary-i386/ Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed InRelease                    
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg [198 B]                 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]       
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed Release.gpg [198 B]        
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release [49.6 kB]                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg [198 B]                    
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                     
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release [49.6 kB]        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release [49.6 kB]                     
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]           
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed Release [49.6 kB]         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources [5,470 B]       
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources [934 kB]              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources [934 kB]                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [14 B]   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [34.0 kB]      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources/DiffIndex                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages/DiffIndex             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages/DiffIndex              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources/DiffIndex                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages/DiffIndex             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages/DiffIndex              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [713 B]  
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [10.2 kB]  
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [122 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources [155 kB]        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources [5,019 kB]        
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
  404  Not Found
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [14 B]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [33.0 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [1,155 B]
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [125 kB] 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources [5,470 B]          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [14 B]
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [33.2 kB]
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [1,394 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages [1,273 kB]     
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages [8,452 B]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages [4,786 kB] 
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages [119 kB] 
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages [1,274 kB]      
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages [8,431 B] 
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages [4,796 kB]  
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [2,073 B]
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [144 kB]      
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [1,058 B]
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [45.8 kB] 
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [346 kB]
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [3,933 B]
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [117 kB]
Get:48 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [2,365 B]
Get:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [349 kB]
Get:50 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [3,949 B]
Get:51 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [117 kB]
Get:52 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [2,540 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Get:53 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources [2,422 B]   
Get:54 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources [14 B]
Get:55 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources [12.4 kB]
Get:56 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources [1,383 B]
Get:57 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages [1,945 B]
Get:58 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages [14 B]
Get:59 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages [11.1 kB]
Get:60 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages [996 B]
Get:61 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages [1,941 B]
Get:62 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:63 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages [11.2 kB]
Get:64 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages [999 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Get:65 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/restricted Sources [1,341 B]
Get:66 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main Sources [65.4 kB]    
Get:67 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/multiverse Sources [14 B] 
Get:68 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/universe Sources [4,241 B]
Get:69 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/restricted amd64 Packages [2,984 B]
Get:70 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main amd64 Packages [152 kB]
Get:71 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/multiverse amd64 Packages [14 B]
Get:72 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/universe amd64 Packages [10.8 kB]
Get:73 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/restricted i386 Packages [3,008 B]
Get:74 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main i386 Packages [153 kB]
Get:75 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/multiverse i386 Packages [14 B]
Get:76 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/universe i386 Packages [10.8 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main TranslationIndex        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/multiverse TranslationIndex  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/restricted TranslationIndex  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/universe TranslationIndex    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/multiverse Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/restricted Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/universe Translation-en      
Fetched 21.7 MB in 25s (851 kB/s)                                              
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9B0BBF00E2D0EBE9
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch [http://ppa.launchpad.net/kamalmostafa/linux-kamal-mjgbacklight/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/kamalmostafa/linux-kamal-mjgbacklight/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/kamalmostafa/linux-kamal-mjgbacklight/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/kamalmostafa/linux-kamal-mjgbacklight/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/kamalmostafa/linux-kamal-mjgbacklight/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/kamalmostafa/linux-kamal-mjgbacklight/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
```

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Moeller on 2012-08-05
This is my result from trying to run the sudo get update through the terminal. Please help.

```


Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/restricted/binary-i386/ InRelease
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/main/binary-i386/ Release
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/restricted/binary-i386/ Release
Err cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/main/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/main/binary-i386/ Translation-en
Err cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/restricted/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/restricted/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425) dists/precise/restricted/binary-i386/ Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed InRelease                    
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg [198 B]                 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]       
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed Release.gpg [198 B]        
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release [49.6 kB]                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg [198 B]                    
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                     
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release [49.6 kB]        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release [49.6 kB]                     
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]           
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed Release [49.6 kB]         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources [5,470 B]       
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources [934 kB]              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources [934 kB]                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [14 B]   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [34.0 kB]      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources/DiffIndex                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages/DiffIndex             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages/DiffIndex              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources/DiffIndex                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages/DiffIndex             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages/DiffIndex              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [713 B]  
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [10.2 kB]  
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [122 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources [155 kB]        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources [5,019 kB]        
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
  404  Not Found
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [14 B]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [33.0 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [1,155 B]
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [125 kB] 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources [5,470 B]          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [14 B]
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [33.2 kB]
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [1,394 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages [1,273 kB]     
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages [8,452 B]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages [4,786 kB] 
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages [119 kB] 
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages [1,274 kB]      
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages [8,431 B] 
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages [4,796 kB]  
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [2,073 B]
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [144 kB]      
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [1,058 B]
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [45.8 kB] 
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [346 kB]
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [3,933 B]
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [117 kB]
Get:48 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [2,365 B]
Get:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [349 kB]
Get:50 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [3,949 B]
Get:51 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [117 kB]
Get:52 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [2,540 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Get:53 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources [2,422 B]   
Get:54 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources [14 B]
Get:55 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources [12.4 kB]
Get:56 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources [1,383 B]
Get:57 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages [1,945 B]
Get:58 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages [14 B]
Get:59 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages [11.1 kB]
Get:60 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages [996 B]
Get:61 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages [1,941 B]
Get:62 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:63 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages [11.2 kB]
Get:64 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages [999 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Get:65 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/restricted Sources [1,341 B]
Get:66 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main Sources [65.4 kB]    
Get:67 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/multiverse Sources [14 B] 
Get:68 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/universe Sources [4,241 B]
Get:69 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/restricted amd64 Packages [2,984 B]
Get:70 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main amd64 Packages [152 kB]
Get:71 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/multiverse amd64 Packages [14 B]
Get:72 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/universe amd64 Packages [10.8 kB]
Get:73 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/restricted i386 Packages [3,008 B]
Get:74 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main i386 Packages [153 kB]
Get:75 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/multiverse i386 Packages [14 B]
Get:76 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/universe i386 Packages [10.8 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main TranslationIndex        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/multiverse TranslationIndex  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/restricted TranslationIndex  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/universe TranslationIndex    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/multiverse Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/restricted Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/universe Translation-en      
Fetched 21.7 MB in 25s (851 kB/s)                                              
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9B0BBF00E2D0EBE9
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch [http://ppa.launchpad.net/kamalmostafa/linux-kamal-mjgbacklight/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/kamalmostafa/linux-kamal-mjgbacklight/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/kamalmostafa/linux-kamal-mjgbacklight/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/kamalmostafa/linux-kamal-mjgbacklight/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/kamalmostafa/linux-kamal-mjgbacklight/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/kamalmostafa/linux-kamal-mjgbacklight/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by oldfred on 2012-08-05
On long outputs from screen or code please use code tags to preserve formating and make it easier to read. Easiest way is to highlight like copying again and click on the # icon in the edit panel above your message.

Edited title to make it a bit more on topic.

It looks like you still have the CD-Rom checked as a source for updates and do not have cd installed.  See my update manager, clicked on settings. I do not have CD checked.

It also looks like you have several other ppas not found. If not valid anymore you should delete or at least comment out.

---

### Post by Moeller on 2012-08-05
My apologies. I am very new to all of this. 

I unchecked the boxes that stated cd rom but on the ppas, how do I know which ones I should remove?

---

### Post by oldfred on 2012-08-05
These seem to be the issues:

```
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9B0BBF00E2D0EBE9
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch http://ppa.launchpad.net/kamalmostaf...source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/kamalmostaf...amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/kamalmostaf...-i386/Packages  404  Not Found


```

---

### Post by Moeller on 2012-08-05
Ok, but what can I do to fix this. Like I said before I have no clue on how to fix this issue.

---

### Post by d4m1r on 2012-08-05
1) ctrl + alt + t

2) sudo software-properties-gtk

3)uncheck the box related to updating/install from CD and kamalmostaf...

---

### Post by Moeller on 2012-08-05
Ok I did that and I still get the error.

---

### Post by oldfred on 2012-08-05
Post just the lines with errors or failed to fetch. Or edit those also.

---

### Post by Moeller on 2012-08-05
This is what I get now.



W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9B0BBF00E2D0EBE9
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0

---

### Post by wildmanne39 on 2012-08-05
*Thread moved to **Absolute Beginner Talk**.*

---

### Post by wildmanne39 on 2012-08-05
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by NikTh on 2012-08-05
Hi , 
try to follow this .

1) Open a terminal and copy-paste below commands 
```
sudo apt-key adv --recv-key --keyserver keyserver.ubuntu.com 9B0BBF00E2D0EBE9
sudo apt-key adv --recv-key --keyserver keyserver.ubuntu.com 5A9A06AEF9CB8DB0
```2)Then write this command
```
gksudo software-properties-gtk
``` and at the opened window go to "Ubuntu Updates" and un-tick CdRom.

3)After that, at the SAME opened window go to "Other Software" and find the PPA with name similar to "kalamostaf.." and delete it.
Close the window and...
4)....at the terminal give 2 below commands
```
sudo rm  /var/lib/apt/lists/* -vf
sudo apt-get update
```**The first command will remove the damaged list and when you run the second command it will replace it with a new list.**

---

### Post by oldos2er on 2012-08-05
Threads merged. Please don't start more than one thread per topic.

---

### Post by Moeller on 2012-08-06
Holy Cow it worked! Thank you so very much!!:D

---

