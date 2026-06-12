---
title: "AUDACITY, my baby wont work, please help!!"
date: 2009-06-29
forum: General Help
---

### Post by sponsoredwalk on 2009-06-29
Hi i'm on Ubuntu 7.10 and after a while i couldn't get the sound to work no matter what i tried so i removed it to re-install and this is what i get...

> sudo apt-get install audacity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  audacity: Depends: libwxgtk2.4-1 (>= 2.4.4.1.1ubuntu2) but it is not installable
E: Broken packages

I can't force the old or new version in synaptic either... please help i'm SO stuck without it... Amabo Te :)

---

### Post by synapsys on 2009-06-29
Try:

```
sudo apt-get build-dep audacity
```

Then try installing.

Or upgrade your version of ubuntu.

---

### Post by sponsoredwalk on 2009-06-29
>  sudo apt-get build-dep audacity
[sudo] password for zxcv:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for audacity


Thanks for that I can't upgrade my pc is too slow and old, i have 256 ram and i can't even use rosegarden without slowing my whole pc, i mean why is it unable to locate if it worked fine before... 
Amabo Te

---

### Post by Monotoko on 2009-06-29
I believe that Ubuntu 7.04 is no longer supported, it no longer has repositories.

There may still be mirrors out there on the net, use google :)

---

### Post by CatKiller on 2009-06-29
> **Monotoko said:**
> I believe that Ubuntu 7.04 is no longer supported, it no longer has repositories.

There may still be mirrors out there on the net, use google :)

Changing instances of archive.ubuntu.com to old-releases.ubuntu.com in sources.list should be sufficient.

---

### Post by sponsoredwalk on 2009-06-29
i'm on 7.10 but how would i change that stuff and where would i get a working version, i srsly have no idea sorry :(, amabo te :)

---

### Post by CatKiller on 2009-06-29
> **sponsoredwalk said:**
> how would i change that stuff

Open a Terminal.

Applications -> Accessories -> Terminal

Open sources.list as root for editing;

```
sudo nano /etc/apt/sources.list
```Enter your password when it asks, even though you won't see anything appear on the line.

This file is a list of locations on the Internet that host packages that you can install. Since the place that holds Feisty Fawn packages has moved, you need to update this list accordingly. You'll see a bunch of lines that look like

```
deb http://_gb.archive_.ubuntu.com/ubuntu/ feisty main
```Change the first part, that I've underlined, so that you end up with something like

```
deb http://old-releases.ubuntu.com/ubuntu/ feisty main
```

(Ctrl-O to save, Ctrl-X to exit, as it says at the bottom of the screen)

Then run ```
sudo apt-get update
``` so that the package management system checks the new location.

---

### Post by sponsoredwalk on 2009-06-29
Just a wild guess but i bet this is not supposed to happen?

> sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Translation-en_IE
Get:2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [189B]                                                                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_IE                                                                            
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy Release.gpg                                                                                          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Translation-en_IE                                                                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg                                                                                             
Get:3 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg [191B]                                                                              
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_IE                                                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_IE                                                                                  
Ign [http://hydr0g3n.free.fr](http://hydr0g3n.free.fr) ./ Release.gpg                                                                                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Translation-en_IE                                                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release                                                                                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_IE                                                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_IE                                                                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_IE                                                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg                                                                                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_IE                                                                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_IE                                                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_IE                                                                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_IE                                                                    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Translation-en_IE                                                                         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy Release                                                                                              
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                                                                              
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [197B]                                                                                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_IE                                                                              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_IE                                                                          
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release                                                                                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg                                                                                    
Get:5 [http://www.bashterritory.com](http://www.bashterritory.com)  Release.gpg [460B]                                                                                      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Packages                                                                                    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                                                                                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Translation-en_IE                                                                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Translation-en_IE                                                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Translation-en_IE                                                                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Translation-en_IE                                                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg                                                                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_IE                                                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_IE                                                                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_IE                                                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_IE                                                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release.gpg                                                                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Translation-en_IE                                                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Translation-en_IE                                                                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Translation-en_IE                                                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Translation-en_IE                                                                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                                                                                 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Packages                                                                                  
Ign [http://hydr0g3n.free.fr](http://hydr0g3n.free.fr) ./ Translation-en_IE                                                                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages                                                                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                                                                                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release                                                                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release                                                                         
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable Release.gpg                                                                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release                                                                                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                                                                                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages                                                                                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                                                                                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages                                                                                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages                                                                                   
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Packages                                                                                    
  404 Not Found
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                                                                                     
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable/non-free Translation-en_IE                                                                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages                                                                            
Get:6 [http://www.bashterritory.com](http://www.bashterritory.com)  Translation-en_IE [460B]                                                                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages                                                                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages                                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages                                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages                                              
Ign [http://hydr0g3n.free.fr](http://hydr0g3n.free.fr) ./ Release                                                                  
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release                                                       
  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Packages  
  404 Not Found
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Packages                                                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Packages                                                                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Packages                                                                            
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                                                                                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Packages                                                                              
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                                                                                           
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages                                                                                     
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                                                                                       
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages                                                                                     
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages                                                                                   
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages                                                                             
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages                                                                               
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages                                                                             
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages                                                                                  
  404 Not Found [IP: 91.189.88.46 80]
Ign [http://hydr0g3n.free.fr](http://hydr0g3n.free.fr) ./ Packages                                                                                                     
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable Release                                                                                                 
Get:7 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release [1005B]                                                                                 
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release                                                                                           
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages                                                                            
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages                                                                              
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages                                                                            
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages                                                                           
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages                                                                                 
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages                                                                           
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages                                                                             
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Packages                                                                            
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Packages                                                                                  
  404 Not Found [IP: 91.189.88.46 80]

---

### Post by CatKiller on 2009-06-29
> **sponsoredwalk said:**
> Just a wild guess but i bet this is not supposed to happen?

No, because you're supposed to have changed all those archive.ubuntu.coms to old-releases.ubuntu.com

EDIT: You might also want to pick just one release. 7.04 was feisty, but you've got dapper (6.06) and gutsy (7.10) entries in there too. That's probably not going to help.

---

### Post by sponsoredwalk on 2009-06-29
OMG THANK YOU!!! Seriously thank you so much, i fixed the > etc/apt/sources.list as best i could, thank you. I'm just wondering though, should I reinstall my sound  or is there a way to fix this problem: It records normally but it seems to stall a few times and that never happened before. Like it goes fine then all of a sudden it will break and go slow for a second... i have tried nice -20 audacity and there is like a tiny bit better change, maybe you would know what is happening...

magna amabo te:)

---

### Post by CatKiller on 2009-06-30
> **sponsoredwalk said:**
> It records normally but it seems to stall a few times and that never happened before. Like it goes fine then all of a sudden it will break and go slow for a second... i have tried nice -20 audacity and there is like a tiny bit better change, maybe you would know what is happening...

No idea at all, I'm afraid. Best start a new thread, I reckon.

---

