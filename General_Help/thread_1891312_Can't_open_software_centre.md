---
title: "Can't open software centre"
date: 2011-12-05
forum: General Help
---

### Post by Spyderkid on 2011-12-05
The Ubuntu software centre for 11.10 has been running fine untill about 4 days ago when it started to refuse to load the software and installed section, I can open the history section :S

The application opens up fine though




I think it may have stopped working after I tried to add the repository gnomenu-team

---

### Post by oldtimer7777 on 2011-12-05
What I would do is uninstall it with the Synaptic Package Manager and reinstall software center. You can use this for now:

sudo apt-get install synaptic
sudo synaptic


> **Spyderkid said:**
> The Ubuntu software centre for 11.10 has been running fine untill about 4 days ago when it started to refuse to load the software and installed section, I can open the history section :S

The application opens up fine though




I think it may have stopped working after I tried to add the repository gnomenu-team

---

### Post by Spyderkid on 2011-12-05
I have synaptic  :D i'm using it as replacement untill the centre is fixed

but i will re-install the centre

---

### Post by Spyderkid on 2011-12-05
tried re-installing, got this error message
```
E: /var/cache/apt/archives/software-center_5.0.2ubuntu0.1_all.deb: trying to overwrite '/usr/share/app-install/desktop', which is also in package app-install-data-partner 12.11.10


```

---

### Post by Old_Grey_Wolf on 2011-12-05
> **Spyderkid said:**
> The Ubuntu software centre for 11.10 has been running fine untill about 4 days ago when it started to refuse to load the software and installed section, I can open the history section :S

The application opens up fine though

I think it may have stopped working after I tried to add the repository gnomenu-team

I think you may have had a "partial update" or a problem with a PPA. 

Please enter these commands in the terminal and post the output ```
sudo apt-get update
``````
sudo apt-get upgrade
```

---

### Post by Old_Grey_Wolf on 2011-12-05
> **oldtimer7777 said:**
> 
sudo apt-get synaptic

That is not a valid command. It doesn't work for me using a VM. I think it is missing the word install. I found the command you gave in a Google search, and it was noted in the replies to the thread that it doesn't work without the install phrase.

I think the solution will require fixing the upgrade rather than re-installing synaptic.

---

### Post by oldos2er on 2011-12-05
> **oldtimer7777 said:**
> sudo synaptic

Graphical applications should be opened with 'gksudo' or 'gksu' rather than 'sudo'.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Spyderkid on 2011-12-06
Run the apt-get's this is what i got (i put what i think is important in red)....

bob@bob-desktop:~$ sudo apt-get update
[COLOR="Red"]Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric InRelease                             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates InRelease                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports InRelease                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease [/COLOR]                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric InRelease                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric Release.gpg                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                    
[COLOR="Red"]Ign [http://deb.opera.com](http://deb.opera.com) stable InRelease   [/COLOR]                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates Release.gpg                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                        
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports Release.gpg                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free i386 Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric Release                               
[COLOR="DarkRed"][COLOR="Red"]Ign [http://dl.google.com](http://dl.google.com) stable InRelease [/COLOR][/COLOR]                                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
[COLOR="Red"]Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex  [/COLOR]                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
[COLOR="Red"]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex [/COLOR]                    
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free i386 Packages               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports Release                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Sources                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Sources                    
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main i386 Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted i386 Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe i386 Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse i386 Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main TranslationIndex                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
[COLOR="Red"]Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free TranslationIndex                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free TranslationIndex       [/COLOR]         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe TranslationIndex             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main Sources                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main i386 Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted i386 Packages      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe i386 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en        
[COLOR="Red"]Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free TranslationIndex   [/COLOR]         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main TranslationIndex         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe TranslationIndex     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main Sources                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted Sources          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse Sources          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main i386 Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted i386 Packages    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe i386 Packages      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main TranslationIndex       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe TranslationIndex   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Translation-en_GB                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Translation-en                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Translation-en_GB          
[COLOR="Red"]Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_GB                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_GB  [/COLOR]                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Translation-en             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Translation-en_GB          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Translation-en             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Translation-en               
[COLOR="Red"]Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en       [/COLOR]                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main Translation-en           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse Translation-en     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main Translation-en         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse Translation-en   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted Translation-en   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe Translation-en     
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_GB                     
[COLOR="Red"]Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en     [/COLOR]                   
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Get:3 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,207 B]
[COLOR="Red"]Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Translation-en_GB               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Translation-en                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Translation-en_GB
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Translation-en
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en[/COLOR]
Fetched 2,752 B in 4s (555 B/s)
Reading package lists... Done
bob@bob-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bob@bob-desktop:~$

---

### Post by oldtimer7777 on 2011-12-06
> **Old_Gray_Wolf said:**
> That is not a valid command. It doesn't work for me using a VM. I think it is missing the word install. I found the command you gave in a Google search, and it was noted in the replies to the thread that it doesn't work without the install phrase.

I think the solution will require fixing the upgrade rather than re-installing synaptic.

Try:

sudo apt-get install synaptic

And see if that works for you now.

---

### Post by oldtimer7777 on 2011-12-06
What I would do is uninstall the software center with Synaptic Package Manager..

sudo apt-get install synaptic

Remove software center and its residual config files with it.

I would run bleachbit. 

sudo apt-get install bleachbit
gksudo bleachbit

Clean out your entire system..

Reinstall software center from synaptic when you are done. 

See if that might help. 

> **Spyderkid said:**
> Run the apt-get's this is what i got (i put what i think is important in red)....

bob@bob-desktop:~$ sudo apt-get update
[COLOR=Red]Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric InRelease                             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates InRelease                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports InRelease                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease [/COLOR]                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric InRelease                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric Release.gpg                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                    
[COLOR=Red]Ign [http://deb.opera.com](http://deb.opera.com) stable InRelease   [/COLOR]                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates Release.gpg                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                        
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports Release.gpg                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free i386 Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric Release                               
[COLOR=DarkRed][COLOR=Red]Ign [http://dl.google.com](http://dl.google.com) stable InRelease [/COLOR][/COLOR]                                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
[COLOR=Red]Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex  [/COLOR]                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
[COLOR=Red]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex [/COLOR]                    
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free i386 Packages               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports Release                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Sources                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Sources                    
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main i386 Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted i386 Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe i386 Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse i386 Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main TranslationIndex                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
[COLOR=Red]Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free TranslationIndex                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free TranslationIndex       [/COLOR]         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe TranslationIndex             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main Sources                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main i386 Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted i386 Packages      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe i386 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en        
[COLOR=Red]Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free TranslationIndex   [/COLOR]         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main TranslationIndex         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe TranslationIndex     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main Sources                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted Sources          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse Sources          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main i386 Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted i386 Packages    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe i386 Packages      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main TranslationIndex       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe TranslationIndex   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Translation-en_GB                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Translation-en                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Translation-en_GB          
[COLOR=Red]Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_GB                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_GB  [/COLOR]                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Translation-en             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Translation-en_GB          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Translation-en             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Translation-en               
[COLOR=Red]Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en       [/COLOR]                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main Translation-en           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse Translation-en     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main Translation-en         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse Translation-en   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted Translation-en   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe Translation-en     
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_GB                     
[COLOR=Red]Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en     [/COLOR]                   
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Get:3 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,207 B]
[COLOR=Red]Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Translation-en_GB               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Translation-en                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Translation-en_GB
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Translation-en
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en[/COLOR]
Fetched 2,752 B in 4s (555 B/s)
Reading package lists... Done
bob@bob-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bob@bob-desktop:~$

---

### Post by Spyderkid on 2011-12-06
> **oldtimer7777 said:**
> Try:

sudo apt-get install synaptic

And see if that works for you now.

I said I tried it and it came up with an error message...

---

### Post by Spyderkid on 2011-12-06
I ran ```
sudo apt-get install bleachbit && gksudo bleachbit
``` and it's cleaned up a load of things :D

---

### Post by oldtimer7777 on 2011-12-06
> **Spyderkid said:**
> I said I tried it and it came up with an error message...

Here is what I would like you to try for us.

Open synaptic package manager.

Click Settings >>> Repositories >>

Change the 'download from' to Main Server.

Click reload and upgrade.

---

### Post by Spyderkid on 2011-12-06
tried that got the same error

---

### Post by oldtimer7777 on 2011-12-06
> **Spyderkid said:**
> tried that got the same error

Could be something fishy with your source.list file.

I would rebuild your source.list file with:

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

gksudo gedit /etc/apt/*sources*.[I]list

Cut and paste over your old source list file contents, save it, and do

sudo apt-get update
sudo apt-get upgrade

If you still see errors.. please post all errors so we can see what they look like.

You may need to reinstall any PPAs you have added besides the ones listed in the source list generation options. 
[/I]

---

### Post by oldos2er on 2011-12-06
> **Spyderkid said:**
> I said I tried it and it came up with an error message...

And the error message is...?

The "Ign" lines you see when running apt-get update mean that particular repository has not received any updates from the last time you ran apt-get update.

---

### Post by oldtimer7777 on 2011-12-06
> **oldos2er said:**
> And the error message is...?

The "Ign" lines you see when running apt-get update mean that particular repository has not received any updates from the last time you ran apt-get update.

I know. They think that is an error. It's not.  For whatever reason they can't uninstall and reinstall software-center completely to flush out whatever is the issue with it.

---

### Post by Spyderkid on 2011-12-06
when i did apt-get update i got quite a few ign's again....

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric InRelease                             
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-security InRelease                    
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-updates InRelease                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
Ign [http://deb.opera.com](http://deb.opera.com) stable InRelease                                      
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-backports InRelease                   
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric Release.gpg                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric InRelease                            
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-security Release.gpg                  
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-updates Release.gpg                   
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-backports Release.gpg                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources                       
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric Release                               
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-security Release                      
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-updates Release                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free i386 Packages                   
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-backports Release                     
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric/main Sources                          
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric/restricted Sources                    
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric/universe Sources                      
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric/main i386 Packages                    
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric/restricted i386 Packages              
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric/universe i386 Packages                
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric/main TranslationIndex                 
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric/universe TranslationIndex             
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-security/main Sources                 
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-security/restricted Sources           
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-security/universe Sources             
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-security/main i386 Packages           
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-security/restricted i386 Packages     
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-security/universe i386 Packages       
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free TranslationIndex                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free i386 Packages               
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-security/main TranslationIndex        
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-security/restricted TranslationIndex  
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-security/universe TranslationIndex    
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-updates/main Sources                  
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-updates/restricted Sources            
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-updates/universe Sources              
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-updates/main i386 Packages            
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-updates/restricted i386 Packages      
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-updates/universe i386 Packages        
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-updates/main TranslationIndex         
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex   
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-updates/universe TranslationIndex     
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-backports/main Sources                
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-backports/restricted Sources          
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-backports/universe Sources            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free TranslationIndex                
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-backports/main i386 Packages          
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-backports/restricted i386 Packages    
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-backports/universe i386 Packages      
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-backports/main TranslationIndex       
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex 
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-backports/universe TranslationIndex   
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric/main Translation-en_GB                
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric/main Translation-en                   
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric/restricted Translation-en_GB          
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric/restricted Translation-en             
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric/universe Translation-en_GB            
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric/universe Translation-en               
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-security/main Translation-en          
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-security/restricted Translation-en    
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-security/universe Translation-en      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free TranslationIndex            
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189 B]                          
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-updates/main Translation-en           
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-updates/restricted Translation-en     
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-updates/universe Translation-en       
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-backports/main Translation-en         
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-backports/restricted Translation-en   
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) oneiric-backports/universe Translation-en     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_GB                    
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_GB             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_GB                     
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en                        
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [2,544 B]                            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Translation-en_GB               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Translation-en                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Translation-en_GB           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Translation-en              
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Get:5 [http://dl.google.com](http://dl.google.com) stable/non-free i386 Packages [1,010 B]             
Ign [http://dl.google.com](http://dl.google.com) stable/non-free TranslationIndex                      
Get:6 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,207 B]                 
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_GB                     
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en                        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Fetched 6,495 B in 17s (362 B/s)

---

### Post by Spyderkid on 2011-12-06
> **oldos2er said:**
> And the error message is...?

The "Ign" lines you see when running apt-get update mean that particular repository has not received any updates from the last time you ran apt-get update.

the error message is on something like my second post?

---

### Post by oldtimer7777 on 2011-12-06
> **Spyderkid said:**
> tried re-installing, got this error message
```
E: /var/cache/apt/archives/software-center_5.0.2ubuntu0.1_all.deb: trying to overwrite '/usr/share/app-install/desktop', which is also in package app-install-data-partner 12.11.10


```

What I usually do when something like this happens is this..

I install Ubuntu Tweak..  I then use Synaptic Package Manager to uninstall whatever software isn't working. 

I use Ubuntu Tweak to clean out the software configuration settings for everything. 

I reboot. 

I run Bleachbit to clean out everything else.

And I reinstall whatever software I uninstalled.

Try that.

Much of the instructions for this is covered here:

[https://debianhelp.wordpress.com/2011/08/02/how-to-maximize-system-performance-in-ubuntu/](https://debianhelp.wordpress.com/2011/08/02/how-to-maximize-system-performance-in-ubuntu/)

---

### Post by Spyderkid on 2011-12-06
already got ubuntu-tweak :D will do...

Also your rebuild the sources list has screwed my google chrome :P

---

### Post by oldos2er on 2011-12-06
Have you tried clearing the cache? ```
sudo apt-get clean
```

---

### Post by Spyderkid on 2011-12-06
I have now, still no progress :S

realised I haven't sent you any screenshots, here's one (it just stays on that loader)

---

### Post by oldtimer7777 on 2011-12-06
> **Spyderkid said:**
> already got ubuntu-tweak :D will do...

Also your rebuild the sources list has screwed my google chrome :P

Yeah it will, that is why I mentioned you need to reinstall your PPAs..

I sure hope you are following my directions correctly. lol

Okay, try

sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean all
sudo apt-get -f update
sudo apt-get -f upgrade

---

### Post by oldtimer7777 on 2011-12-06
> **oldos2er said:**
> Have you tried clearing the cache? ```
sudo apt-get clean
```

That's why I gave him this link.. He needs to make sure to clean out his entire system first from top to bottom:

[https://debianhelp.wordpress.com/2011/08/02/how-to-maximize-system-performance-in-ubuntu/](https://debianhelp.wordpress.com/2011/08/02/how-to-maximize-system-performance-in-ubuntu/)

Otherwise we won't be able to figure out what's wrong and they will be s.o.l.

---

### Post by Spyderkid on 2011-12-06
> **oldtimer7777 said:**
> yeah it will, that is why i mentioned you need to reinstall your ppas..

I sure hope you are following my directions correctly. Lol

okay, try

sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean all
sudo apt-get -f update
sudo apt-get -f upgrade

done! :D

---

### Post by oldtimer7777 on 2011-12-06
> **Spyderkid said:**
> done! :D

Reboot your system.. 

try opening software center from the command line, and cut and paste any errors you find in command line while it is starting up... you will be able to actually visualize what is happening during the startup of software center when you invoke the software center command from the command line.. the command line will display all the processes that go into starting software center (even when it hangs)    Comes in kinda helpful when things hang like this.

It should look like this:

```
linuxxx@linuxxxx-Satellite-xxx:~$ software-center
2011-12-06 12:02:56,552 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/db/database.py', 154, 'open')'
2011-12-06 12:02:56,552 - root - WARNING - failed to add sca db Couldn't stat '/home/linux555/.cache/software-center/software-center-agent.db' (No such file or directory)
/usr/share/software-center/softwarecenter/app.py:1194: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self.window_main.show_all()
2011-12-06 12:02:57,732 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/pymodules/python2.7/zeitgeist/client.py', 367, 'reconnect_monitors')'
2011-12-06 12:02:57,732 - zeitgeist.client - INFO - Reconnected to Zeitgeist engine...
/usr/share/software-center/softwarecenter/SimpleGtkbuilderApp.py:50: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  gtk.main()
^CTraceback (most recent call last):
  File "/usr/share/software-center/update-software-center-agent", line 85, in <module>
    if not update_from_software_center_agent(db, cache, options.ignore_etag, include_approved_but_unpublished):
  File "/usr/share/software-center/softwarecenter/db/update.py", line 467, in update_from_software_center_agent
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/backend/channel.py", line 153, in _check_for_channel_updates_timer
    time.sleep(0.1)
KeyboardInterrupt
    if self._check_for_channel_updates():
  File "/usr/share/software-center/softwarecenter/backend/channel.py", line 169, in _check_for_channel_updates
    cache_origins = self.db._aptcache.get_origins()
  File "/usr/share/software-center/softwarecenter/apt/aptcache.py", line 177, in get_origins
    for item in pkg.candidate.origins:
  File "/usr/lib/python2.7/dist-packages/apt/package.py", line 442, in origins
    origins.append(Origin(self.package, packagefile))
  File "/usr/lib/python2.7/dist-packages/apt/package.py", line 151, in __init__
    indexfile = pkg._pcache._list.find_index(packagefile)
KeyboardInterrupt
2011-12-06 12:03:04,930 - softwarecenter.app - INFO - software-center-agent finished with status 1

```

---

### Post by Spyderkid on 2011-12-06
ran software-center

```
bob@bob-desktop:~$ software-center
2011-12-06 19:19:21,924 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 15 21
2011-12-06 19:19:26,729 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2011-12-06 19:19:26,840 - softwarecenter.ui.gtk3.utils - INFO - Softwarecenter style provider for ambiance Gtk theme: /usr/share/software-center/ui/gtk3/css/softwarecenter.css
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1193, in show_lobby
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 125, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 109, in init_view
    SoftwarePane.init_view(self)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/softwarepane.py", line 261, in init_view
    self.icons, self.show_ratings)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/appview.py", line 76, in __init__
    self.helper = AppPropertiesHelper(db, cache, icons)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/models/appstore2.py", line 228, in __init__
    softwarecenter.paths.APP_INSTALL_PATH)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 106, in parse_applications_menu
    tree = ET.parse(f)
  File "/usr/lib/python2.7/xml/etree/ElementTree.py", line 1177, in parse
    tree.parse(source, parser)
  File "/usr/lib/python2.7/xml/etree/ElementTree.py", line 646, in parse
    source = open(source, "rb")
IOError: [Errno 20] Not a directory: '/usr/share/app-install/desktop/software-center.menu'
2011-12-06 19
```

---

### Post by oldtimer7777 on 2011-12-06
Can you please disable your current themed desktop back to the original default theme that comes with Ubuntu 11.10? 

See if Software Center will open for you then...

> **Spyderkid said:**
> ran software-center

```
bob@bob-desktop:~$ software-center
2011-12-06 19:19:21,924 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 15 21
2011-12-06 19:19:26,729 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2011-12-06 19:19:26,840 - softwarecenter.ui.gtk3.utils - INFO - Softwarecenter style provider for ambiance Gtk theme: /usr/share/software-center/ui/gtk3/css/softwarecenter.css
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1193, in show_lobby
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 125, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 109, in init_view
    SoftwarePane.init_view(self)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/softwarepane.py", line 261, in init_view
    self.icons, self.show_ratings)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/appview.py", line 76, in __init__
    self.helper = AppPropertiesHelper(db, cache, icons)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/models/appstore2.py", line 228, in __init__
    softwarecenter.paths.APP_INSTALL_PATH)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 106, in parse_applications_menu
    tree = ET.parse(f)
  File "/usr/lib/python2.7/xml/etree/ElementTree.py", line 1177, in parse
    tree.parse(source, parser)
  File "/usr/lib/python2.7/xml/etree/ElementTree.py", line 646, in parse
    source = open(source, "rb")
IOError: [Errno 20] Not a directory: '/usr/share/app-install/desktop/software-center.menu'
2011-12-06 19
```

---

### Post by oldos2er on 2011-12-06
> **oldtimer7777 said:**
> [https://debianhelp.wordpress.com/2011/08/02/how-to-maximize-system-performance-in-ubuntu/](https://debianhelp.wordpress.com/2011/08/02/how-to-maximize-system-performance-in-ubuntu/)


I don't see what any of that has to do with the problem, aside from cleaning the APT cache.

Edit: On closer examination, there are some problems with the advice given in that blog. Startupmanager is no longer under development; the only version of Ubuntu Tweak that will work on 11.10 is alpha level software and probably shouldn't be recommended without caveats; the blogger is unaware that Gnome GUI programs need to be called with 'gksudo' not sudo; etc.

Spyderkid, it looks as though this bug is your problem: [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/891499](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/891499)

---

### Post by Old_Grey_Wolf on 2011-12-06
Try entering these commands in the terminal ```
sudo rm -rf /var/lib/apt/lists/*

sudo apt-get update

sudo apt-get dist-upgrade
```

Of course post any errors you get.

---

### Post by oldtimer7777 on 2011-12-06
You can run synaptic with the sudo command. That was the way I was always taught to do it, but if you prefer that I use gksudo instead, I certainly will.  You don't have to be uptight about it. Sheish..If you don't like the link that I provided, that is your opinion, however to debug a problem like the one this user is experiencing usually cleaning the system out as much as possible first, is part of the process of elimination to discover whatever is causing this issue with Ubuntu software center. Ubuntu Tweak is in alpha, but so what? Everything here is basically in development, including 11.10..  What is your probem exactly? > **oldos2er said:**
> I don't see what any of that has to do with the problem, aside from cleaning the APT cache.
 
Edit: On closer examination, there are some problems with the advice given in that blog. Startupmanager is no longer under development; the only version of Ubuntu Tweak that will work on 11.10 is alpha level software and probably shouldn't be recommended without caveats; the blogger is unaware that Gnome GUI programs need to be called with 'gksudo' not sudo; etc.
 
Spyderkid, it looks as though this bug is your problem: [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/891499](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/891499)

---

### Post by Spyderkid on 2011-12-07
> **oldos2er said:**
> I don't see what any of that has to do with the problem, aside from cleaning the APT cache.

Edit: On closer examination, there are some problems with the advice given in that blog. Startupmanager is no longer under development; the only version of Ubuntu Tweak that will work on 11.10 is alpha level software and probably shouldn't be recommended without caveats; the blogger is unaware that Gnome GUI programs need to be called with 'gksudo' not sudo; etc.

Spyderkid, it looks as though this bug is your problem: [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/891499](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/891499)

that's definatly my bug

---

### Post by Spyderkid on 2011-12-07
> **Old_Gray_Wolf said:**
> Try entering these commands in the terminal ```
sudo rm -rf /var/lib/apt/lists/*

sudo apt-get update

sudo apt-get dist-upgrade
```

Of course post any errors you get.

I ran the first two, no errors.

Didn't run the third because i didn't know what it did?

---

### Post by Old_Grey_Wolf on 2011-12-07
> **Spyderkid said:**
> I ran the first two, no errors.

Didn't run the third because i didn't know what it did?

You can run ```
sudo apt-get upgrade
``` instead of the third commend; however, it doesn't do some updates. "upgrade" is used to install the newest versions of all packages currently installed on the system. "dist-upgrade", in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages.

---

### Post by Spyderkid on 2011-12-08
ran all the 3 commands, no errors

---

### Post by Spyderkid on 2011-12-08
found out something...

the software-center is dependent on ubuntu-desktop however

ubuntu-desktop package is broken, so I marked it for complete removal in synaptic, and it was successfully removed, however....

I tried to install it straight after, but it came up with errors saying that I can't install it, now I can't even open the software center...

the errors were...

"E: /var/cache/apt/archives/software-center_5.0.2ubuntu0.1_all.deb: trying to overwrite '/usr/share/app-install/desktop', which is also in package app-install-data-partner 12.11.10"

and this.....
```
(Reading database ... 224661 files and directories currently installed.)
Preparing to replace software-center 5.0.2ubuntu0.1 (using .../software-center_5.0.2ubuntu0.1_all.deb) ...
Unpacking replacement software-center ...
dpkg: error processing /var/cache/apt/archives/software-center_5.0.2ubuntu0.1_all.deb (--unpack):
 trying to overwrite '/usr/share/app-install/desktop', which is also in package app-install-data-partner 12.11.10
No apport report written because MaxReports has already been reached
                                                                    Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for hicolor-icon-theme ...
Errors were encountered while processing:
 /var/cache/apt/archives/software-center_5.0.2ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on software-center; however:
  Package software-center is not installed.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ubuntu-desktop


```

---

### Post by Spyderkid on 2011-12-08
also ran sudo dpkg --configure -a

came up with some errors....


bob@bob-desktop~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on software-center; however:
  Package software-center is not installed.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ubuntu-desktop

---

### Post by Old_Grey_Wolf on 2011-12-08
I don't like to give this advice; however, it looks like you installed and old PPA, ran all sorts of commands suggested in forums, and things are getting worse. Maybe it is time to make a copy of /home to an external media, then start over with a fresh install, and restore your important files from the copy of /home that you need; such as, Documents, Music, Pictures, etc.
:(

---

### Post by Spyderkid on 2011-12-09
I will use the blessings of UbuntuOne and will install, i'm going to use synaptic for now however till I feel like re-installing

---

### Post by Spyderkid on 2011-12-10
[SIZE="3"]OMG! I FIXED IT![/SIZE]

I was just using google-chrome and a window popped up saying that I needed a parshal distro upgrade!

I did it, and all the things that were broken are fixed includeing the software center

WOOP WOOP!

---

