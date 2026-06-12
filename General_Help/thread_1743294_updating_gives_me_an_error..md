---
title: "updating gives me an error."
date: 2011-04-29
forum: General Help
---

### Post by slgtheindividual on 2011-04-29
When I run "sudo apt-get update" it takes ages to perform and then I get back a huge error ( I think it's due to old PPA's from 11.04 beta but I dont know which or how to get rid of them, and I don't wanna risk losing anything important) any help would be appreciated

" ~$ sudo apt-get update
Ign [http://deb.opera.com](http://deb.opera.com) lenny InRelease
Hit [http://deb.opera.com](http://deb.opera.com) lenny Release.gpg                                                                                                                                                      
Ign [http://download.virtualbox.org](http://download.virtualbox.org) natty InRelease                                                                                                                                              
Hit [http://deb.opera.com](http://deb.opera.com) lenny Release                                                                                                                                                           
Hit [http://deb.opera.com](http://deb.opera.com) lenny/non-free i386 Packages                                                                                                                                                
Hit [http://download.virtualbox.org](http://download.virtualbox.org) natty Release.gpg                                                                                                                                             
Ign [http://deb.opera.com](http://deb.opera.com) lenny/non-free TranslationIndex                                                                                                                                         
Hit [http://download.virtualbox.org](http://download.virtualbox.org) natty Release                                                                                                                                                 
Hit [http://download.virtualbox.org](http://download.virtualbox.org) natty/contrib i386 Packages                                                                                                                                       
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                                                                                                                                        
Ign [http://download.virtualbox.org](http://download.virtualbox.org) natty/contrib TranslationIndex                                                                                                                                
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197 B]                                                                                                                                            
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                                                                                                                                              
Get:3 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,064 B]                                                                                                                                       
Ign [http://deb.opera.com](http://deb.opera.com) lenny/non-free Translation-en_GB                                                                                                                                            
Ign [http://deb.opera.com](http://deb.opera.com) lenny/non-free Translation-en                                                                                                                                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                                                                                                                                     
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                                                                                                                                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                                                                                                             
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                                                                                                                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                                                                                                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                                                                                                                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                                                                                                                                             
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources                                                                                                                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                                                                                                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                                                                                                               
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                                                                                                            
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                                                                                                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_GB                                                                                                                  
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_GB                                                                                                           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                                                                                                                     
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                                                                                                              
Ign [http://download.virtualbox.org](http://download.virtualbox.org) natty/contrib Translation-en_GB                                                                                                         
Ign [http://download.virtualbox.org](http://download.virtualbox.org) natty/contrib Translation-en                                                                                      
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                                                                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                                                            
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                                                                                                                                         
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                                             
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                                             
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease           
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease           
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease           
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease           
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease           
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg         
  Unable to connect to ppa.launchpad.net:http:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg         
  Unable to connect to ppa.launchpad.net:http:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg         
  Unable to connect to ppa.launchpad.net:http:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg         
  Unable to connect to ppa.launchpad.net:http:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg         
  Unable to connect to ppa.launchpad.net:http:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg         
  Unable to connect to ppa.launchpad.net:http:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg         
  Unable to connect to ppa.launchpad.net:http:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg         
  Unable to connect to ppa.launchpad.net:http:
Err [http://ubuntu.datahop.net](http://ubuntu.datahop.net) natty InRelease          
  
Err [http://ubuntu.datahop.net](http://ubuntu.datahop.net) natty-updates InRelease  
  
Err [http://ubuntu.datahop.net](http://ubuntu.datahop.net) natty-backports InRelease
  
Err [http://ubuntu.datahop.net](http://ubuntu.datahop.net) natty-security InRelease 
  
Err [http://ubuntu.datahop.net](http://ubuntu.datahop.net) natty-proposed InRelease 
  
Err [http://ubuntu.datahop.net](http://ubuntu.datahop.net) natty Release.gpg        
  Unable to connect to ubuntu.datahop.net:http:
Err [http://ubuntu.datahop.net](http://ubuntu.datahop.net) natty-updates Release.gpg
  Unable to connect to ubuntu.datahop.net:http:
Err [http://ubuntu.datahop.net](http://ubuntu.datahop.net) natty-backports Release.gpg
  Unable to connect to ubuntu.datahop.net:http:
Err [http://ubuntu.datahop.net](http://ubuntu.datahop.net) natty-security Release.gpg
  Unable to connect to ubuntu.datahop.net:http:
Err [http://ubuntu.datahop.net](http://ubuntu.datahop.net) natty-proposed Release.gpg
  Unable to connect to ubuntu.datahop.net:http:
Fetched 2,608 B in 2min 0s (22 B/s)
Reading package lists... Done
W: Failed to fetch [http://ubuntu.datahop.net/ubuntu/dists/natty/InRelease](http://ubuntu.datahop.net/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://ubuntu.datahop.net/ubuntu/dists/natty-updates/InRelease](http://ubuntu.datahop.net/ubuntu/dists/natty-updates/InRelease)  

W: Failed to fetch [http://ubuntu.datahop.net/ubuntu/dists/natty-backports/InRelease](http://ubuntu.datahop.net/ubuntu/dists/natty-backports/InRelease)  

W: Failed to fetch [http://ubuntu.datahop.net/ubuntu/dists/natty-security/InRelease](http://ubuntu.datahop.net/ubuntu/dists/natty-security/InRelease)  

W: Failed to fetch [http://ubuntu.datahop.net/ubuntu/dists/natty-proposed/InRelease](http://ubuntu.datahop.net/ubuntu/dists/natty-proposed/InRelease)  

W: Failed to fetch [http://ppa.launchpad.net/chromium-daily/stable/ubuntu/dists/natty/InRelease](http://ppa.launchpad.net/chromium-daily/stable/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/natty/InRelease](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/natty/InRelease](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/natty/InRelease](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/natty/InRelease](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/natty/InRelease](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://ppa.launchpad.net/unity/ppa/ubuntu/dists/natty/InRelease](http://ppa.launchpad.net/unity/ppa/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu/dists/natty/InRelease](http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://ppa.launchpad.net/chromium-daily/stable/ubuntu/dists/natty/Release.gpg](http://ppa.launchpad.net/chromium-daily/stable/ubuntu/dists/natty/Release.gpg)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/natty/Release.gpg](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/natty/Release.gpg)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/natty/Release.gpg](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/natty/Release.gpg)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/natty/Release.gpg](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/natty/Release.gpg)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/natty/Release.gpg](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/natty/Release.gpg)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/natty/Release.gpg](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/natty/Release.gpg)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/unity/ppa/ubuntu/dists/natty/Release.gpg](http://ppa.launchpad.net/unity/ppa/ubuntu/dists/natty/Release.gpg)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu/dists/natty/Release.gpg](http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu/dists/natty/Release.gpg)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ubuntu.datahop.net/ubuntu/dists/natty/Release.gpg](http://ubuntu.datahop.net/ubuntu/dists/natty/Release.gpg)  Unable to connect to ubuntu.datahop.net:http:

W: Failed to fetch [http://ubuntu.datahop.net/ubuntu/dists/natty-updates/Release.gpg](http://ubuntu.datahop.net/ubuntu/dists/natty-updates/Release.gpg)  Unable to connect to ubuntu.datahop.net:http:

W: Failed to fetch [http://ubuntu.datahop.net/ubuntu/dists/natty-backports/Release.gpg](http://ubuntu.datahop.net/ubuntu/dists/natty-backports/Release.gpg)  Unable to connect to ubuntu.datahop.net:http:

W: Failed to fetch [http://ubuntu.datahop.net/ubuntu/dists/natty-security/Release.gpg](http://ubuntu.datahop.net/ubuntu/dists/natty-security/Release.gpg)  Unable to connect to ubuntu.datahop.net:http:

W: Failed to fetch [http://ubuntu.datahop.net/ubuntu/dists/natty-proposed/Release.gpg](http://ubuntu.datahop.net/ubuntu/dists/natty-proposed/Release.gpg)  Unable to connect to ubuntu.datahop.net:http:

W: Some index files failed to download. They have been ignored, or old ones used instead."

---

### Post by jbroome on 2011-04-29
Looks like there's a networking issue with launchpad repos.  I'm having the same issue and popped in here to see if there was an explanation up.

---

### Post by KegHead on 2011-04-29
Hi!

The servers might be overwhelmed!

Try:

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -

sudo apt-get install linux-image -f

Restart.

Advise.

KegHead

---

### Post by whalogreg on 2011-04-29
> **jbroome said:**
> Looks like there's a networking issue with launchpad repos.  I'm having the same issue and popped in here to see if there was an explanation up.

same..

---

### Post by DavidCHill on 2011-04-29
Same here.  Problem started yesterday.

---

### Post by DavidCHill on 2011-04-29
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/773381](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/773381)

I don't know if it's a bug or something... but still.

---

### Post by slgtheindividual on 2011-04-29
> **KegHead said:**
> Hi!

The servers might be overwhelmed!

Try:

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -

sudo apt-get install linux-image -f

Restart.

Advise.

KegHead

Did this, ran update again and errors went, did it again and they came back, confusingly.

---

### Post by DavidCHill on 2011-04-29
Seems like it would be an issue with launchpad.

---

### Post by tjk on 2011-04-29
Anyone found out what's going on?  I searched launchpad.net for info, but there was no indication that they had a problem...

---

### Post by DavidCHill on 2011-04-29
> **DavidCHill said:**
> [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/773381](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/773381)

I don't know if it's a bug or something... but still.

Seems like launchpad has a problem.

People with 10.10 are experiencing the same issue.

---

### Post by DavidCHill on 2011-04-29
> **DavidCHill said:**
> Seems like launchpad has a problem.

People with 10.10 are experiencing the same issue.

10.04 sorry.

---

### Post by M4570D0N on 2011-04-29
I'm having the same issue. I am able to connect to Ubuntu/Linux Mint repos. It's only my PPAs that fail to connect to Launchpad (and it's every PPA, not just some of my PPAs).

---

### Post by sprockboy on 2011-04-29
I have a problem too.. :/  I don't know what to do...

> Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty InRelease                               
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty-updates InRelease                       
Obj [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                      
Obj [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty Release.gpg                             
Obj [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Obj [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty-updates Release.gpg                     
Obj [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Obj [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty Release                                 
Obj [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources               
Obj [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                 
Obj [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources               
Obj [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages               
Obj [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages         
Obj [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Obj [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty-updates Release                         
Obj [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages           
Obj [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Obj [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Obj [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty/main Sources                            
Obj [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty/restricted Sources                      
Obj [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty/universe Sources                        
Obj [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty/multiverse Sources                      
Obj [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty/main i386 Packages                      
Obj [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources                         
Obj [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty/restricted i386 Packages                
Obj [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty/universe i386 Packages                  
Obj [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty/multiverse i386 Packages                
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty/universe TranslationIndex               
Obj [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty-updates/main Sources                    
Obj [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty-updates/restricted Sources              
Obj [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty-updates/universe Sources                
Obj [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Obj [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty-updates/multiverse Sources              
Obj [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty-updates/main i386 Packages              
Obj [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty-updates/restricted i386 Packages        
Obj [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty-updates/universe i386 Packages          
Obj [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty-updates/multiverse i386 Packages        
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Obj [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty/main Translation-es                     
Obj [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty/multiverse Translation-es               
Obj [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty/restricted Translation-es               
Obj [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty/universe Translation-es                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-es_VE           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-es              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-es_VE     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-es        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-es_VE     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-es        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-es_VE       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-es          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Obj [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                 
Obj [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Obj [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Obj [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-es_VE               
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-es                  
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-es_VE                      
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty/main Translation-es_VE                  
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty/main Translation-en                     
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty/multiverse Translation-es_VE           
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty/multiverse Translation-en              
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty/restricted Translation-es_VE           
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty/restricted Translation-en              
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty/universe Translation-es_VE             
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty/universe Translation-en                
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty-updates/main Translation-es_VE         
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty-updates/main Translation-es            
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty-updates/main Translation-en            
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty-updates/multiverse Translation-es_VE   
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty-updates/multiverse Translation-es      
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty-updates/multiverse Translation-en      
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty-updates/restricted Translation-es_VE   
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty-updates/restricted Translation-es      
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty-updates/restricted Translation-en      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-es                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                        
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty-updates/universe Translation-es_VE     
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty-updates/universe Translation-es        
Ign [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) natty-updates/universe Translation-en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease        
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease        
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease        
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease        
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg      
  No se pudo conectar a ppa.launchpad.net:http:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg
  No se pudo conectar a ppa.launchpad.net:http:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg
  No se pudo conectar a ppa.launchpad.net:http:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg
  No se pudo conectar a ppa.launchpad.net:http:
Leyendo lista de paquetes... Hecho
W: Imposible obtener [http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu/dists/natty/InRelease](http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu/dists/natty/InRelease)  

W: Imposible obtener [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/natty/InRelease](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/natty/InRelease)  

W: Imposible obtener [http://ppa.launchpad.net/rye/ubuntuone-extras/ubuntu/dists/natty/InRelease](http://ppa.launchpad.net/rye/ubuntuone-extras/ubuntu/dists/natty/InRelease)  

W: Imposible obtener [http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/natty/InRelease](http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/natty/InRelease)  

W: Imposible obtener [http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu/dists/natty/Release.gpg](http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu/dists/natty/Release.gpg)  No se pudo conectar a ppa.launchpad.net:http:

W: Imposible obtener [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/natty/Release.gpg](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/natty/Release.gpg)  No se pudo conectar a ppa.launchpad.net:http:

W: Imposible obtener [http://ppa.launchpad.net/rye/ubuntuone-extras/ubuntu/dists/natty/Release.gpg](http://ppa.launchpad.net/rye/ubuntuone-extras/ubuntu/dists/natty/Release.gpg)  No se pudo conectar a ppa.launchpad.net:http:

W: Imposible obtener [http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/natty/Release.gpg](http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/natty/Release.gpg)  No se pudo conectar a ppa.launchpad.net:http:

W: Algunos archivos de índice fallaron al descargar. Se han ignorado, o se han utilizado unos antiguos en su lugar


---

### Post by slgtheindividual on 2012-05-16
For me the problem solved itself after a few days. I'm going to mark this thread as solved so anybody who still has this issue feel free to pm me and I'll unmark it.

---

