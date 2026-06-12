---
title: "Just upgraded to 11.10 help on ppa ??"
date: 2011-10-16
forum: General Help
---

### Post by Kiraitachi on 2011-10-16
HI I just updated to Ubuntu 11.10 and the problem is that some ppa's are disabled cause of upgrade....already enabled them and everythinh but I think I deleted some important ppa's that come out with ubuntu 11.10 so plz could someone post a screener with the default ppa 11.10? or just post them here???

Thanks.

And another question what are the Ubuntu ppa backports for? should I add them to Ubuntu 11.10

---

### Post by jemadux on 2011-10-16
a good way to use ppa is to run "ubuntu tweak "

---

### Post by Kiraitachi on 2011-10-16
I know that already the problem is that i dint know what ppa,s did buntu 11.10 did ship as default, so i can add them again

---

### Post by gandaran on 2011-10-16
> could someone post a screener with the default ppa 11.10? or just post them here???
I don't know what you mean but ubuntu doesn't have any defaults PPA, you install the ones you want and some that did work for older ubuntu releases don't work on 11.10.
so if you want some application only found on some PPA use google search for the same application name + PPA, it'l come up on the search and lead you to the launchpad PPA.

> And another question what are the Ubuntu ppa backports for? should I add them to Ubuntu 11.10
that is a bad option, use only backports if you really need to install some application, backports updates may break your system.

---

### Post by Kiraitachi on 2011-10-16
> **gandaran said:**
> I don't know what you mean but ubuntu doesn't have any defaults PPA, you install the ones you want and some that did work for older ubuntu releases don't work on 11.10.
so if you want some application only found on some PPA use google search for the same application name + PPA, it'l come up on the search and lead you to the launchpad PPA.


that is a bad option, use only backports if you really need to install some application, backports updates may break your system.

[IMG]http://s2.subirimagenes.com/imagen/previo/thump_7034377screenshot-at-201110.png[/IMG]

If u cant see it it is attached also, the ppa below are custom I added but the 4 first are the ones that already comes with Ubuntu, I deleted a couple of them I think by mistake...not sure...anyway I get a couple of error of 404 when updating with terminal in SUdo apt-get update

---

### Post by gandaran on 2011-10-16
> with Ubuntu, I deleted a couple of them I think by mistake...not sure...anyway I get a couple of error of 404 when updating with terminal in SUdo apt-get update
check which the ones output the error 404 and remove them as they no longer work

---

### Post by Kiraitachi on 2011-10-16
Hi look this is why Im asking the ppa thing cause when I update I get errors...not sure if its because many people are updating at same time since 11.10 just came out :/ or its my settings ....

[SPOILER]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                  
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric InRelease                  
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates InRelease           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                       
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]            
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main amd64 Packages             
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner amd64 Packages      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en             
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US   
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en      
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-security InRelease
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages
  404  Not Found
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric Release.gpg
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates Release.gpg
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-security Release.gpg
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric Release                               
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates Release                       
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-security Release                      
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/main Sources                          
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/restricted Sources                    
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/universe Sources                      
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/multiverse Sources                    
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/main amd64 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/restricted amd64 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/universe amd64 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/multiverse amd64 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/main i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/restricted i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/universe i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/multiverse i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/main TranslationIndex
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/multiverse TranslationIndex
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/restricted TranslationIndex
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/universe TranslationIndex
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/main Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/restricted Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/universe Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/multiverse Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/main amd64 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/restricted amd64 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/universe amd64 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/multiverse amd64 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/main i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/restricted i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/universe i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/main TranslationIndex
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-security/main Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-security/restricted Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-security/universe Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-security/multiverse Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-security/main amd64 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-security/restricted amd64 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-security/universe amd64 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-security/multiverse amd64 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-security/main i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-security/restricted i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-security/universe i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-security/multiverse i386 Packages
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-security/main TranslationIndex
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-security/multiverse TranslationIndex
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-security/restricted TranslationIndex
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-security/universe TranslationIndex
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/main Translation-en
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/multiverse Translation-en
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/restricted Translation-en
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric/universe Translation-en
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/main Translation-en
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-updates/universe Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-security/main Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-security/main Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-security/multiverse Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-security/multiverse Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-security/restricted Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-security/restricted Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-security/universe Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) oneiric-security/universe Translation-en
Fetched 72 B in 2min 29s (0 B/s)
W: Failed to fetch [http://ppa.launchpad.net/ackondro/tibesti/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/ackondro/tibesti/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ackondro/tibesti/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/ackondro/tibesti/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ackondro/tibesti/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/ackondro/tibesti/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
[/SPOILER]

---

