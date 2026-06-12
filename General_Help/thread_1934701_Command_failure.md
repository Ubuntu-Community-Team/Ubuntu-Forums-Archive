---
title: "Command failure"
date: 2012-03-02
forum: General Help
---

### Post by Miykel on 2012-03-02
G'Day;  I'm trying to run the following command;

sudo apt-add-repository ‘deb [http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-v3.5.13/ubuntu](http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-v3.5.13/ubuntu) oneiric main’
   But when I do I get an error message "need repository as argument', as i have no idea what that means is there someone here who can help please.
OS is Ubuntu 11.10
Regards Miykel   :confused:

---

### Post by matt_symes on 2012-03-02
Hi

You are mixing two different ways of adding a repository to you sources.

You need

```
sudo bash -c "echo deb http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-v3.5.13/ubuntu oneiric main >> /etc/apt/sources.list"
```

then

```
sudo apt-key adv --keyserver keyserver.quickbuild.pearsoncomputing.net --recv-keys 2B8638D0
```

and

```
sudo apt-get update
```

Taken from this link.

[http://trinitydesktop.org/installation.php](http://trinitydesktop.org/installation.php)

Kind regards

---

### Post by Miykel on 2012-03-03
Thanks so much Matt_Symes; I used the commands you suggested and went to the site in the link you supplied and run the commands with each;

deb [http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-v3.5.13/ubuntu](http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-v3.5.13/ubuntu) oneiric main deb-src [http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-v3.5.13/ubuntu](http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-v3.5.13/ubuntu) oneiric main deb [http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps-v3.5.13/ubuntu](http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps-v3.5.13/ubuntu) oneiric main deb-src [http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps-v3.5.13/ubuntu](http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps-v3.5.13/ubuntu) oneiric mainwhich seemed to work ok, I guess, but when I tried to install Trinity i run these commands, from the site,

sudo apt-get update sudo apt-get install kubuntu-default-settings-trinity kubuntu-desktop-trinityquite a few of the files (?) could not be found (error 404) and when I run the last command I got error message "default settings not found "
Been trying to install Trinity for about a week now, maybe it just doesn't work in 11.10.
Thanks again for the time you've taken to try to help.
Kind Regards Miykel

---

### Post by matt_symes on 2012-03-03
Hi

I am surprised it did not work as these are their instructions. 

I will have a go at installing it tomorrow and tell you how i get on.

EDIT:

Can you try it again but post back the output of the

```
sudo apt-get install ..
```

commands.

Post the output between code tags like this

[noparse]```
output
```[/noparse]

to get output like this

```
output
```

It's much easier to read. I want to know what files are missing (404)

Kind regards

---

### Post by Miykel on 2012-03-03
Thanks for the trouble your taking Matt_Symes; Folowing is the output of the terminal ( I Hope) lol.

[miykel@miykel-H61M-USB3-B3:~$ Sudo bash -c "echo deb [http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-v3.5.13/ubuntu](http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-v3.5.13/ubuntu) oneiric main"
No command 'Sudo' found, did you mean:
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
 Command 'udo' from package 'udo' (universe)
Sudo: command not found
miykel@miykel-H61M-USB3-B3:~$ sudo bash -c "echo deb [http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-v3.5.13/ubuntu](http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-v3.5.13/ubuntu) oneiric main"
[sudo] password for miykel: 
deb [http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-v3.5.13/ubuntu](http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-v3.5.13/ubuntu) oneiric main
miykel@miykel-H61M-USB3-B3:~$ sudo bash -c "echo deb-src [http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-v3.5.13/ubuntu](http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-v3.5.13/ubuntu) oneiric main"
deb-src [http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-v3.5.13/ubuntu](http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-v3.5.13/ubuntu) oneiric main
miykel@miykel-H61M-USB3-B3:~$ sudo bash -c "echo deb [http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps-v3.5.13/ubuntu](http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps-v3.5.13/ubuntu) oneiric main"
deb [http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps-v3.5.13/ubuntu](http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps-v3.5.13/ubuntu) oneiric main
miykel@miykel-H61M-USB3-B3:~$ sudo bash -c "echo deb-src [http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps-v3.5.13/ubuntu](http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps-v3.5.13/ubuntu) oneiric main"
deb-src [http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps-v3.5.13/ubuntu](http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps-v3.5.13/ubuntu) oneiric main
miykel@miykel-H61M-USB3-B3:~$ sudo apt-key adv --keyserver keyserver.quickbuild.pearsoncomputing.net --recv-keys 2B8638D0
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.9pGRIxa2Cv --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.quickbuild.pearsoncomputing.net --recv-keys 2B8638D0
gpg: requesting key 2B8638D0 from hkp server keyserver.quickbuild.pearsoncomputing.net
gpg: key 2B8638D0: "QuickBuild Trinity Desktop Environment" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
miykel@miykel-H61M-USB3-B3:~$ sudo apt-get update
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Release
Err cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognised by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Translation-en_AU
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Translation-en
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric InRelease                             
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates InRelease                     
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-backports InRelease                   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric Release.gpg                           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates Release.gpg                   
Ign [http://ppa.quickbuild.pearsoncumputing.net](http://ppa.quickbuild.pearsoncumputing.net) oneiric InRelease               
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-backports Release.gpg                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric Release                               
Err [http://ppa.quickbuild.pearsoncumputing.net](http://ppa.quickbuild.pearsoncumputing.net) oneiric Release.gpg             
  Something wicked happened resolving 'ppa.quickbuild.pearsoncumputing.net:http' (-5 - No address associated with hostname)
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates Release                       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-backports Release                     
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/main Sources                          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/restricted Sources                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/universe Sources                      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/multiverse Sources                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/main amd64 Packages                   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/restricted amd64 Packages             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/universe amd64 Packages               
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/multiverse amd64 Packages             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.quickbuild.pearsoncumputing.net](http://ppa.quickbuild.pearsoncumputing.net) oneiric Release                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/main i386 Packages                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/restricted i386 Packages              
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/universe i386 Packages                
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/multiverse i386 Packages              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/main TranslationIndex                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/universe TranslationIndex             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/main Sources                  
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/restricted Sources            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/universe Sources              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/multiverse Sources            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/main amd64 Packages           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/restricted amd64 Packages     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/universe amd64 Packages       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/multiverse amd64 Packages     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/main i386 Packages            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/restricted i386 Packages      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/universe i386 Packages        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/main TranslationIndex         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/universe TranslationIndex     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-backports/main Sources                
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg [198 B]          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-backports/restricted Sources          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-backports/universe Sources            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric InRelease                            
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]                      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-backports/multiverse Sources          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-backports/main amd64 Packages         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-backports/restricted amd64 Packages   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-backports/universe amd64 Packages     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-backports/multiverse amd64 Packages   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-backports/main i386 Packages          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-backports/restricted i386 Packages    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-backports/universe i386 Packages      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-backports/main TranslationIndex       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-backports/universe TranslationIndex   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/main Translation-en_AU                
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/main Translation-en                   
Ign [http://ppa.quickbuild.pearsoncumputing.net](http://ppa.quickbuild.pearsoncumputing.net) oneiric/main TranslationIndex   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/multiverse Translation-en_AU          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/multiverse Translation-en             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/restricted Translation-en_AU          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/restricted Translation-en             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/universe Translation-en               
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/main Translation-en           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/multiverse Translation-en     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/restricted Translation-en     
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release [40.8 kB]            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/universe Translation-en       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-backports/main Translation-en         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner amd64 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-backports/multiverse Translation-en   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-backports/restricted Translation-en   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-backports/universe Translation-en     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free amd64 Packages                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Ign [http://ppa.quickbuild.pearsoncomputing.net](http://ppa.quickbuild.pearsoncomputing.net) oneiric InRelease               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free amd64 Packages              
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources [31.8 kB]       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources/DiffIndex                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main amd64 Packages/DiffIndex               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main i386 Packages/DiffIndex                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main TranslationIndex                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free i386 Packages                   
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources [14 B]    
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources [11.4 kB]   
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources [1,645 B] 
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main amd64 Packages [84.4 kB]
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
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free i386 Packages               
Err [http://ppa.quickbuild.pearsoncumputing.net](http://ppa.quickbuild.pearsoncumputing.net) oneiric/main Sources            
  Something wicked happened resolving 'ppa.quickbuild.pearsoncumputing.net:http' (-5 - No address associated with hostname)
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted amd64 Packages [14 B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe amd64 Packages [29.1 kB]
Err [http://ppa.quickbuild.pearsoncumputing.net](http://ppa.quickbuild.pearsoncumputing.net) oneiric/main amd64 Packages     
  Something wicked happened resolving 'ppa.quickbuild.pearsoncumputing.net:http' (-5 - No address associated with hostname)
Err [http://ppa.quickbuild.pearsoncumputing.net](http://ppa.quickbuild.pearsoncumputing.net) oneiric/main i386 Packages      
  Something wicked happened resolving 'ppa.quickbuild.pearsoncumputing.net:http' (-5 - No address associated with hostname)
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse amd64 Packages [3,190 B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free TranslationIndex                
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages [84.4 kB]
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_AU             
Err [http://ppa.quickbuild.pearsoncumputing.net](http://ppa.quickbuild.pearsoncumputing.net) oneiric/main Translation-en_AU  
  Something wicked happened resolving 'ppa.quickbuild.pearsoncumputing.net:http' (-5 - No address associated with hostname)
Err [http://ppa.quickbuild.pearsoncumputing.net](http://ppa.quickbuild.pearsoncumputing.net) oneiric/main Translation-en     
  Something wicked happened resolving 'ppa.quickbuild.pearsoncumputing.net:http' (-5 - No address associated with hostname)
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages [14 B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages [29.1 kB]
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free TranslationIndex            
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages [3,355 B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex [73 B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex [72 B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex [70 B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex [73 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_AU                    
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en [47.2 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en [20.3 kB]
Ign [http://ppa.quickbuild.pearsoncomputing.net](http://ppa.quickbuild.pearsoncomputing.net) oneiric InRelease               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main amd64 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main i386 Packages                          
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                       
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
  404  Not Found
Ign [http://ppa.quickbuild.pearsoncomputing.net](http://ppa.quickbuild.pearsoncomputing.net) oneiric Release.gpg             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_AU                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_AU                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_AU                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_AU                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_AU          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Get:22 [http://ppa.quickbuild.pearsoncomputing.net](http://ppa.quickbuild.pearsoncomputing.net) oneiric Release.gpg [316 B]  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Translation-en_AU               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Translation-en                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Translation-en_AU           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Translation-en              
Ign [http://ppa.quickbuild.pearsoncomputing.net](http://ppa.quickbuild.pearsoncomputing.net) oneiric Release                 
Hit [http://ppa.quickbuild.pearsoncomputing.net](http://ppa.quickbuild.pearsoncomputing.net) oneiric Release           
Ign [http://ppa.quickbuild.pearsoncomputing.net](http://ppa.quickbuild.pearsoncomputing.net) oneiric/main TranslationIndex
Hit [http://ppa.quickbuild.pearsoncomputing.net](http://ppa.quickbuild.pearsoncomputing.net) oneiric/main Sources      
Hit [http://ppa.quickbuild.pearsoncomputing.net](http://ppa.quickbuild.pearsoncomputing.net) oneiric/main amd64 Packages
Hit [http://ppa.quickbuild.pearsoncomputing.net](http://ppa.quickbuild.pearsoncomputing.net) oneiric/main i386 Packages
Ign [http://ppa.quickbuild.pearsoncomputing.net](http://ppa.quickbuild.pearsoncomputing.net) oneiric/main TranslationIndex
Err [http://ppa.quickbuild.pearsoncomputing.net](http://ppa.quickbuild.pearsoncomputing.net) oneiric/main amd64 Packages
  404  Not Found
Err [http://ppa.quickbuild.pearsoncomputing.net](http://ppa.quickbuild.pearsoncomputing.net) oneiric/main i386 Packages
  404  Not Found
Ign [http://ppa.quickbuild.pearsoncomputing.net](http://ppa.quickbuild.pearsoncomputing.net) oneiric/main Translation-en_AU
Ign [http://ppa.quickbuild.pearsoncomputing.net](http://ppa.quickbuild.pearsoncomputing.net) oneiric/main Translation-en
Ign [http://ppa.quickbuild.pearsoncomputing.net](http://ppa.quickbuild.pearsoncomputing.net) oneiric/main Translation-en_AU
Ign [http://ppa.quickbuild.pearsoncomputing.net](http://ppa.quickbuild.pearsoncomputing.net) oneiric/main Translation-en
Fetched 388 kB in 3min 59s (1,621 B/s)
W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognised by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch [http://ppa.quickbuild.pearsoncumputing.net/trinity/trinity-v3.5.13/ubuntu/dists/oneiric/Release.gpg](http://ppa.quickbuild.pearsoncumputing.net/trinity/trinity-v3.5.13/ubuntu/dists/oneiric/Release.gpg)  Something wicked happened resolving 'ppa.quickbuild.pearsoncumputing.net:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ppa.quickbuild.pearsoncumputing.net/trinity/trinity-v3.5.13/ubuntu/dists/oneiric/main/source/Sources](http://ppa.quickbuild.pearsoncumputing.net/trinity/trinity-v3.5.13/ubuntu/dists/oneiric/main/source/Sources)  Something wicked happened resolving 'ppa.quickbuild.pearsoncumputing.net:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ppa.quickbuild.pearsoncumputing.net/trinity/trinity-v3.5.13/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.quickbuild.pearsoncumputing.net/trinity/trinity-v3.5.13/ubuntu/dists/oneiric/main/binary-amd64/Packages)  Something wicked happened resolving 'ppa.quickbuild.pearsoncumputing.net:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ppa.quickbuild.pearsoncumputing.net/trinity/trinity-v3.5.13/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.quickbuild.pearsoncumputing.net/trinity/trinity-v3.5.13/ubuntu/dists/oneiric/main/binary-i386/Packages)  Something wicked happened resolving 'ppa.quickbuild.pearsoncumputing.net:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ppa.quickbuild.pearsoncumputing.net/trinity/trinity-v3.5.13/ubuntu/dists/oneiric/main/i18n/Translation-en_AU](http://ppa.quickbuild.pearsoncumputing.net/trinity/trinity-v3.5.13/ubuntu/dists/oneiric/main/i18n/Translation-en_AU)  Something wicked happened resolving 'ppa.quickbuild.pearsoncumputing.net:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ppa.quickbuild.pearsoncumputing.net/trinity/trinity-v3.5.13/ubuntu/dists/oneiric/main/i18n/Translation-en](http://ppa.quickbuild.pearsoncumputing.net/trinity/trinity-v3.5.13/ubuntu/dists/oneiric/main/i18n/Translation-en)  Something wicked happened resolving 'ppa.quickbuild.pearsoncumputing.net:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ppa.launchpad.net/killeroid/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/killeroid/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/killeroid/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/killeroid/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/killeroid/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/killeroid/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.quickbuild.pearsoncomputing.net/trinity-v3.5.13/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.quickbuild.pearsoncomputing.net/trinity-v3.5.13/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.quickbuild.pearsoncomputing.net/trinity-v3.5.13/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.quickbuild.pearsoncomputing.net/trinity-v3.5.13/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
miykel@miykel-H61M-USB3-B3:~$ sudo apt-get install kubuntu-default-settings-trinity kubuntu-desktop-trinity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package kubuntu-default-settings-trinity
E: Unable to locate package kubuntu-desktop-trinity
miykel@miykel-H61M-USB3-B3:~$ ]

I hope you can make sense of it, I already have Oxygen installed, which was simple and taught me nothing, I hope I'll learn heaps with this drama.
Regards  Miykel

---

### Post by matt_symes on 2012-03-05
Hi

Sorry for the late reply. Your problem lies here.

> W: Failed to fetch [http://ppa.launchpad.net/killeroid/p...source/Sources](http://ppa.launchpad.net/killeroid/p...source/Sources) 404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/killeroid/p...amd64/Packages](http://ppa.launchpad.net/killeroid/p...amd64/Packages) 404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/killeroid/p...-i386/Packages](http://ppa.launchpad.net/killeroid/p...-i386/Packages) 404 Not Found

W: Failed to fetch [http://ppa.quickbuild.pearsoncomputi...amd64/Packages](http://ppa.quickbuild.pearsoncomputi...amd64/Packages) 404 Not Found

W: Failed to fetch [http://ppa.quickbuild.pearsoncomputi...-i386/Packages](http://ppa.quickbuild.pearsoncomputi...-i386/Packages) 404 Not Found

It cannot find the ppas and, because of that, it cannot find the packages you are trying to install.

I will take a look after Lunch.

Kind regards

---

### Post by matt_symes on 2012-03-05
Hi

Can you post the output of

```
cat /etc/apt/sources.list
```

Please try to use code tags. It makes it much easier to read.

I want to take a look at your sources file.

Kind regards

---

