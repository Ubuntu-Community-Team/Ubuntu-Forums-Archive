---
title: "Update problem with ubuntu 11.04 &quot;Unable to parse package file&quot;"
date: 2011-09-09
forum: General Help
---

### Post by carloona on 2011-09-09
Hi,

I am getting the following error while updating using ubuntu 11.04: 


E: Unable to parse package file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_i18n_Index (1)

same thing is happening while I try to update from update manager, or try to install any software.

I am using Ubuntu main server for update and tried changing it to some other server, but then some other error messages occur.

Is there any way out?

---

### Post by raja.genupula on 2011-09-09
```
sudo rm -rf /var/lib/apt/lists/*
```
```
sudo apt-get update
```

let us know what you got

---

### Post by carloona on 2011-09-09
Here is the output when I tried that: 

carloona@carloona-laptop:~$ sudo rm -rf /var/lib/apt/lists/*
carloona@carloona-laptop:~$ sudo apt-get update
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                        
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease                        
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Get:2 [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg [198 B]         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates InRelease                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security InRelease               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                         
Get:3 [http://archive.canonical.com](http://archive.canonical.com) natty Release [5,916 B]           
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release [9,753 B]                         
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release.gpg [198 B]               
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg [316 B]                       
Get:7 [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources [4,157 B]             
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release.gpg [198 B]              
Get:9 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources [14 B]             
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg [316 B]                      
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security Release.gpg [198 B]            
Get:12 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages [14 B]                
Get:13 [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages [8,649 B]      
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg [316 B]                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Get:15 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg [316 B]                      
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release [9,762 B]              
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release [39.8 kB]                       
Get:18 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release [9,730 B]                        
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release [31.4 kB]               
Get:20 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release [9,741 B]                        
Get:21 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release [9,744 B]                        
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security Release [31.4 kB]              
Get:23 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources [1,601 B]                   
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Sources [4,104 B]            
Get:25 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages [1,434 B]             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_IN                      
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse Sources [155 kB]             
Get:27 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex [635 B]            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_IN               
Get:28 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources [1,920 B]                   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Get:29 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages [1,520 B]
99% [29 Packages bzip2 0 B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex               
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main i386 Packages [14 B]       
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe i386 Packages [1,890 B]
Get:32 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages [568 B]       
99% [32 Packages bzip2 0 B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse i386 Packages [24.9 kB]
Get:34 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex [529 B]    
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main TranslationIndex [104 kB]
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse TranslationIndex [14 B]
Get:37 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages [1,678 B]
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted TranslationIndex [315 kB]
Get:39 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_IN [2,852 B]
54% [39 Translation-en_IN bzip2 0 B] [38 TranslationIndex 64.0 kB/315 kB 20%] [bzip2: (stdin) is not a bzip2 file.
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe TranslationIndex [90.9 kB]     
Get:41 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_IN [824 B]           
41% [41 Translation-en_IN bzip2 0 B] [Waiting for headers] [Waiting for headersbzip2: (stdin) is not a bzip2 file.
Get:42 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Sources [4,258 B]    
Get:43 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en [5,537 B]            
42% [43 Translation-en xz 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/xz: (stdin): File format not recognized
Get:44 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main i386 Packages [14 B]  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
  404  Not Found
Get:45 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe i386 Packages [650 B]  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
  404  Not Found
Get:46 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse i386 Packages [10.6 kB]
Get:47 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main TranslationIndex [66.2 kB] 
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
  404  Not Found
Get:48 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse TranslationIndex [14 B]
Get:49 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted TranslationIndex [174 kB]
E: Unable to parse package file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_i18n_Index (1)

Looks the same as before :(

---

### Post by raja.genupula on 2011-09-09
hey
 please  give me your source list by using this 

```
sudo gedit /etc/apt/sources.list
```

---

### Post by carloona on 2011-09-09
sources.list:

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty restricted main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty restricted multiverse universe main #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates restricted main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates restricted multiverse universe main #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security restricted main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security restricted multiverse universe main #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

---

### Post by raja.genupula on 2011-09-09
ok 
first copy this original to some location 

then do this place '#' at these lines and try again in the source , i mean 

```
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates restricted main
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates restricted multiverse universe main #Added by software-properties
```

let me know what you got

---

### Post by carloona on 2011-09-09
Here is the output:

Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                        
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                      
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates InRelease                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security InRelease                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release.gpg [198 B]              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security Release.gpg                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages [1,434 B]              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_IN                      
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex [635 B]             
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_IN               
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release [31.4 kB]                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources [1,920 B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security Release                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Sources                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse Sources
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages [1,520 B]
98% [6 Packages bzip2 0 B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex              
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main i386 Packages [14 B]       
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages [568 B]       
98% [8 Packages bzip2 0 B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe i386 Packages [1,890 B]
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex [529 B]   
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse i386 Packages [24.9 kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main TranslationIndex [105 kB]  
Get:13 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages [1,678 B]
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_IN [2,852 B]         
72% [14 Translation-en_IN bzip2 0 B] [12 TranslationIndex 58.5 kB/105 kB 55%] [bzip2: (stdin) is not a bzip2 file.
E: Unable to parse package file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Index (1)

---

### Post by raja.genupula on 2011-09-09
sorry for late just now i am back from class 

have taken the back up your original sources . 
do update again with this modification 

```
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty restricted main
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty restricted multiverse universe main #Added by software-properties
```

---

### Post by raja.genupula on 2011-09-09
[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/160579](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/160579)

& 

[http://sathyasays.com/2009/11/08/how-to-fix-e-unable-to-parse-package-file-varlibaptextended_states-1-error-in-synaptic-or-apt-get/](http://sathyasays.com/2009/11/08/how-to-fix-e-unable-to-parse-package-file-varlibaptextended_states-1-error-in-synaptic-or-apt-get/)


let me know what you got

---

### Post by carloona on 2011-09-09
Thanks for your help. But unfortunately none of them worked. After I ran the codes given in the lunchpad link mentioned by you the output looks like:


carloona@carloona-laptop:~$ LANG=C;sudo apt-get update
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates InRelease                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                       
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security InRelease               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release.gpg                                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                            
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release.gpg              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                                      
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security Release.gpg                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release                                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security Release                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Sources                                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse Sources                                                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                                                  
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages [1434 B]                           
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main i386 Packages [14 B]                                                   
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex [635 B]                                                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_IN                                  
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_IN                           
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe i386 Packages [1890 B]
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources [1920 B]                                                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                                                           
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                              
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse i386 Packages [24.9 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex 
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main TranslationIndex [105 kB]  
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages [1520 B]
34% [8 Packages bzip2 0 B] [7 TranslationIndex 16.1 kB/105 kB 15%] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                                
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages [568 B]                         
93% [9 Packages bzip2 0 B] [7 TranslationIndex 96.8 kB/105 kB 92%] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
E: Unable to parse package file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Index (1)

carloona@carloona-laptop:~$ LANG=C;sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


similar was the output from other two methods, that same error message at the end. :(

---

