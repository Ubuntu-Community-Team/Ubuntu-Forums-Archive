---
title: "unstable system"
date: 2009-12-16
forum: General Help
---

### Post by andres-bracho on 2009-12-16
I don't know what happened but since the last update my system is very unstable. I have some apps that are not in the ubuntu repositories (or approved) that are not working: Frostwire, Instabird, RadicalCodex, Rainlendar... it opens but if I try to change something (preferences) it collapses...

But it's not only those apps... Pidgin have the same behavior. even Audacious changed it preferences by itself and I don't know which option was (it is remembering last played songs).

At this very moment, I'm writing using Chrome, because Firefox do not load... there is a Firefox's zombie process that I don't know how to remove, and if I try to run it a popup say that is already running...

Games are not running in the right screen size anymore (they are bigger than my current screen so I can't see borders, that mean, menus) and are moving veeery slow (this games were good just a week ago)

To explain it in another way, it looks like if I had a virus... I know this is Linux, but everything is happening so strange, like if I had a virus back in my old windows days... BTW, I have clamav...   ; )

What should I do? (please don't say reinstall)

This is Ubuntu 9.10 upgraded from 9.04 upgraded from 8.10 runing in Acer Aspire 9300, AMD Athlon 64x2, 80 Gb HD, 2 Gb DDR2 RAM, 528 Mb NVidia GeForce Go 6100.

Thanks in advance.

---

### Post by andres-bracho on 2009-12-16
Uh! and Nicotine-Plus is also collapsing just when finishing searching...   :(

---

### Post by andres-bracho on 2009-12-16
Multiget does not save files in the given location... it says that it doesn't have permission and save on .multiget, but in fact it is saving in the right place, just warning that it can't.

Gnome panel crashes each time I close some app that use icons in the notification area.

And I can't set preferences (rightclick) in the notes using the sticky notes applet.

Finally... I'm sorry, English is not my main language, when I say "collapses" I mean that Crashes...

---

### Post by snowpine on 2009-12-16
Hi, what's the output of the following commands please?

```
cat /etc/apt/sources.list
sudo apt-get update
```

---

### Post by andres-bracho on 2009-12-16
andres@MegaMovil:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://download.skype.com/linux/repos/debian](http://download.skype.com/linux/repos/debian) stable non-free #skype
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) karmic main #ubuntu-tweak
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) karmic main #GNome Themes
deb [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) karmic main #unetbootin
# deb-src [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) karmic main #unetbootin (desactivado en la actualización a karmic)
deb [http://linux.getdropbox.com/ubuntu](http://linux.getdropbox.com/ubuntu) karmic main #DropBox
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) karmic non-free #VirtualBox
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) karmic-getdeb games #GetDeb Games
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) karmic-getdeb apps #GetDeb Apps
andres@MegaMovil:~$ sudo apt-get update
[sudo] password for andres: 
Des:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                           
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-es                        
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-es             
Obj [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) karmic Release.gpg                            
Obj [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) karmic/main Translation-es                    
Ign [http://linux.getdropbox.com](http://linux.getdropbox.com) karmic Release.gpg                             
Ign [http://linux.getdropbox.com](http://linux.getdropbox.com) karmic/main Translation-es                     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-es                            
Ign [http://download.skype.com](http://download.skype.com) stable Release.gpg                               
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-es                        
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-es                        
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-es                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-es       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-es         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-es       
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-es                        
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Obj [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) karmic/restricted Translation-es              
Obj [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) karmic/universe Translation-es                
Obj [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) karmic/multiverse Translation-es              
Obj [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) karmic-updates Release.gpg                    
Obj [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-es                 
Ign [http://linux.getdropbox.com](http://linux.getdropbox.com) karmic Release                                 
Ign [http://download.skype.com](http://download.skype.com) stable/non-free Translation-es                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-es                        
Obj [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release.gpg                          
Ign [http://linux.getdropbox.com](http://linux.getdropbox.com) karmic/main Packages                           
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-es                        
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Obj [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                   
Obj [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb Release.gpg                        
Ign [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/games Translation-es               
Ign [http://linux.getdropbox.com](http://linux.getdropbox.com) karmic/main Packages                           
Ign [http://download.skype.com](http://download.skype.com) stable Release                                   
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Obj [http://linux.getdropbox.com](http://linux.getdropbox.com) karmic/main Packages                           
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages             
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                    
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources              
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages               
Ign [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) karmic-updates/main Translation-es            
Ign [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) karmic-updates/restricted Translation-es      
Ign [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) karmic-updates/universe Translation-es        
Obj [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Ign [http://download.virtualbox.org](http://download.virtualbox.org) karmic/non-free Translation-es              
Ign [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/apps Translation-es                
Obj [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb Release                            
Obj [http://download.skype.com](http://download.skype.com) stable/non-free Packages                         
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources                
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages             
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources              
Ign [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) karmic-updates/multiverse Translation-es      
Obj [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) karmic Release                                
Obj [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources                        
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Obj [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/games Packages                     
Obj [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release                              
Obj [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) karmic-updates Release                        
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources                               
Obj [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/apps Packages                      
Obj [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) karmic/main Packages                          
Obj [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) karmic/restricted Packages                    
Obj [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) karmic/main Sources                           
Obj [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) karmic/restricted Sources                     
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Obj [http://download.virtualbox.org](http://download.virtualbox.org) karmic/non-free Packages                    
Obj [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) karmic/universe Packages                      
Obj [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) karmic/universe Sources                       
Obj [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) karmic/multiverse Packages                    
Obj [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) karmic/multiverse Sources                     
Obj [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) karmic-updates/main Packages                  
Obj [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) karmic-updates/restricted Packages            
Obj [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) karmic-updates/main Sources                   
Obj [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) karmic-updates/restricted Sources             
Obj [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) karmic-updates/universe Packages              
Obj [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) karmic-updates/universe Sources               
Obj [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) karmic-updates/multiverse Packages            
Obj [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) karmic-updates/multiverse Sources             
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-es                        
Des:2 [http://dl.google.com](http://dl.google.com) stable Release [2540B]         
Des:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [866B]     
Des:4 [http://dl.google.com](http://dl.google.com) stable/non-free Packages [1010B]                    
Obj [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-es                        
Obj [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Obj [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Descargados 4605B en 8s (574B/s)                                                                                                                                                
Leyendo lista de paquetes... Hecho
andres@MegaMovil:~$

---

### Post by snowpine on 2009-12-16
Hi Andres, you have added several 3rd party software sources to the list (including a Skype repository that's not even for Ubuntu). I would recommend removing these extra software sources and using only the official Ubuntu repositories **if** stability is your #1 concern. It is your decision though.

Good luck!

---

### Post by andres-bracho on 2009-12-16
Ok, I'm going to remove as much as possible...

Thank you!

---

