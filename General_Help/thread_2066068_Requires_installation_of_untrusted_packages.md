---
title: "Requires installation of untrusted packages"
date: 2012-10-03
forum: General Help
---

### Post by gpsvn on 2012-10-03
Ubuntu tells me to update, then tell me something is wrong. I am confused.

> The action would require the installation of packages from not authenticated sources.

libc-bin libc-dev-bin libc6 libc6-dev multiarch-support nvidia-common

---

### Post by oldos2er on 2012-10-03
Can you post the complete output from ```
sudo apt-get update
``` ?

---

### Post by cortman on 2012-10-03
This just means you've likely lost an encryption key for one of the Ubuntu repositories- the output of the command given by oldos2er will help us figure that out.

---

### Post by gpsvn on 2012-10-04
> **oldos2er said:**
> Can you post the complete output from ```
sudo apt-get update
``` ?

Thank you oldos2er.

I ran the command from terminal and it seems to be ok. Then I clicked on the Update Manager again, it ran without popping up an error message.

I am not sure if you still need to outputs, but here it is.

Thanks again.

```
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease
Ign [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise InRelease                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Ign [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-backports InRelease         
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                       
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise Release.gpg                           
Get:3 [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Get:5 [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-backports Release.gpg [198 B]       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:6 [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [48.7 kB]       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Get:8 [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-backports Release [49.6 kB]         
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise InRelease                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [1,950 B] 
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [14.5 kB]  
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,386 B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [178 kB] 
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise/main Sources                          
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise/universe Sources                      
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise/universe TranslationIndex             
Get:13 [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-updates/main Sources [172 kB]      
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise InRelease                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [3,968 B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [48.6 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,369 B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [73 B]
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [71 B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [71 B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Get:21 [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-updates/restricted Sources [3,285 B]
Get:22 [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-updates/universe Sources [58.0 kB] 
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Get:23 [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-updates/multiverse Sources [4,241 B]
Get:24 [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-updates/main i386 Packages [403 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release      
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main TranslationIndex
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages
Get:25 [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-updates/restricted i386 Packages [6,732 B]
Get:26 [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-updates/universe i386 Packages [143 kB]
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main TranslationIndex
Get:27 [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-updates/multiverse i386 Packages [9,673 B]
Get:28 [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:29 [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:30 [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:31 [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise/main Translation-en                   
Get:32 [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-backports/main Sources [2,422 B]   
Get:33 [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-backports/restricted Sources [14 B]
Get:34 [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-backports/universe Sources [15.1 kB]
Get:35 [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-backports/multiverse Sources [2,669 B]
Get:36 [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-backports/main i386 Packages [1,941 B]
Get:37 [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:38 [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-backports/universe i386 Packages [13.7 kB]
Get:39 [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-backports/multiverse i386 Packages [2,504 B]
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-backports/restricted Translation-en   
Hit [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com) precise-backports/universe Translation-en     
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_US           
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_US
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en
Fetched 1,299 kB in 24s (52.2 kB/s)
Reading package lists... Done

```

---

### Post by cortman on 2012-10-04
Looks like apt-get update was all you needed to run- everything's fine now.
Please mark the thread [SOLVED] using the thread tools in the upper right.
Good luck!

---

### Post by raja.genupula on 2012-10-04
> **gpsvn said:**
> Ubuntu tells me to update, then tell me something is wrong. I am confused.

Hmm @OP 

ok you will get this type of messages when ever you are installing pkg from Third party sources .
So while you going like that you should know what you are installing .. you can install them by giving yes or y  by trying to do from terminal . .

---

### Post by vkadal on 2012-10-07
When I try to install any package, I am getting this error message. I ran apt-get  update. I am copying the error message part alone.

W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures were invalid: BADSIG A040830F7FAC5991 Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: BADSIG 531EE72F4C9D234C Launchpad webupd8
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Can anyone figure out the problem?

---

### Post by cortman on 2012-10-08
Yes, it's an easy fix- follow the instructions given [here]("http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/").

---

