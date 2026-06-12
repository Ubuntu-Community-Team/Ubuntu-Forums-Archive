---
title: "Unknown error..."
date: 2009-07-01
forum: General Help
---

### Post by TSWMIN85 on 2009-07-01
I keep getting this error:

> W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://deb.opera.com](http://deb.opera.com) lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAA
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE
W: You may want to run apt-get update to correct these problems
 whenever I run:

```
 sudo get-apt get update
```or whenever I push the check button in my Update Manager.

Thanks in advance!

---

### Post by colau on 2009-07-01
> **TSWMIN85 said:**
> I keep getting this error:

 whenever I run:

```
 sudo get-apt get update
```or whenever I push the check button in my Update Manager.

Thanks in advance!
It's not error but warning.
Can you post
```

cat /etc/apt/sources.list

```

---

### Post by TSWMIN85 on 2009-07-01
[HTML]john@laptop:~$ cat /etc/apt/sources.list
# Salimane Adjao Moustapha's Ubuntu Jaunty Jackalope 9.04 Sources list
#
# Repository List based on standard Jaunty with many extra packages
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number):
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you have a gpg key URL use (replace URL with the key address):
#
# wget -q http://lut1n.ifrance.com/repo_key.asc -O- | sudo apt-key add -
#
# If you have a gpg key file use (replace FILE with the key file):
#
# sudo apt-key add FILE
# Ubuntu supported packages
deb http://fr.archive.ubuntu.com/ubuntu/ jaunty main restricted multiverse universe
deb http://fr.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb http://fr.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted multiverse universe
deb http://fr.archive.ubuntu.com/ubuntu/ jaunty-security main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu jaunty-proposed main restricted universe multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu/ jaunty main restricted multiverse universe
deb-src http://fr.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted multiverse universe
deb-src http://fr.archive.ubuntu.com/ubuntu/ jaunty-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-proposed main restricted universe multiverse
#Canonical Commercial Repository
deb http://archive.canonical.com/ubuntu jaunty partner
deb http://archive.canonical.com/ubuntu jaunty-backports partner
deb http://archive.canonical.com/ubuntu jaunty-updates partner
deb http://archive.canonical.com/ubuntu jaunty-security partner
deb http://archive.canonical.com/ubuntu jaunty-proposed partner
deb-src http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty-backports partner
deb-src http://archive.canonical.com/ubuntu jaunty-updates partner
deb-src http://archive.canonical.com/ubuntu jaunty-security partner
deb-src http://archive.canonical.com/ubuntu jaunty-proposed partner
#gnome-globalmenu
deb http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu jaunty main
#opera
deb http://deb.opera.com/opera/ lenny non-free
#skype
deb http://download.skype.com/linux/repos/debian stable non-free
#firefox
deb http://ppa.launchpad.net/fta/ubuntu jaunty main
#gnome-do
deb http://ppa.launchpad.net/do-core/ubuntu jaunty main
#compiz-fusion
deb http://ppa.launchpad.net/compiz/ubuntu jaunty main
#google
deb http://dl.google.com/linux/deb/ stable non-free
#medibuntu
deb http://packages.medibuntu.org/ jaunty free non-free
# MySQL Workbench
deb ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/ binary/
deb-src ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/ source/
# Depot PlayOnLinux
deb http://deb.playonlinux.com/ jaunty main
# Ubuntu tweak
deb http://ppa.launchpad.net/tualatrix/ubuntu jaunty main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu jaunty main
##Themes du ZgegBlog: Project Bisigi
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main
john@laptop:~$ 

[/HTML]

---

### Post by colau on 2009-07-01
> **TSWMIN85 said:**
> [HTML]john@laptop:~$ cat /etc/apt/sources.list
# Salimane Adjao Moustapha's Ubuntu Jaunty Jackalope 9.04 Sources list
#
# Repository List based on standard Jaunty with many extra packages
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number):
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you have a gpg key URL use (replace URL with the key address):
#
# wget -q http://lut1n.ifrance.com/repo_key.asc -O- | sudo apt-key add -
#
# If you have a gpg key file use (replace FILE with the key file):
#
# sudo apt-key add FILE
# Ubuntu supported packages
deb http://fr.archive.ubuntu.com/ubuntu/ jaunty main restricted multiverse universe
deb http://fr.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb http://fr.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted multiverse universe
deb http://fr.archive.ubuntu.com/ubuntu/ jaunty-security main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu jaunty-proposed main restricted universe multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu/ jaunty main restricted multiverse universe
deb-src http://fr.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted multiverse universe
deb-src http://fr.archive.ubuntu.com/ubuntu/ jaunty-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-proposed main restricted universe multiverse
#Canonical Commercial Repository
deb http://archive.canonical.com/ubuntu jaunty partner
deb http://archive.canonical.com/ubuntu jaunty-backports partner
deb http://archive.canonical.com/ubuntu jaunty-updates partner
deb http://archive.canonical.com/ubuntu jaunty-security partner
deb http://archive.canonical.com/ubuntu jaunty-proposed partner
deb-src http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty-backports partner
deb-src http://archive.canonical.com/ubuntu jaunty-updates partner
deb-src http://archive.canonical.com/ubuntu jaunty-security partner
deb-src http://archive.canonical.com/ubuntu jaunty-proposed partner
#gnome-globalmenu
deb http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu jaunty main
#opera
deb http://deb.opera.com/opera/ lenny non-free
#skype
deb http://download.skype.com/linux/repos/debian stable non-free
#firefox
deb http://ppa.launchpad.net/fta/ubuntu jaunty main
#gnome-do
deb http://ppa.launchpad.net/do-core/ubuntu jaunty main
#compiz-fusion
deb http://ppa.launchpad.net/compiz/ubuntu jaunty main
#google
deb http://dl.google.com/linux/deb/ stable non-free
#medibuntu
deb http://packages.medibuntu.org/ jaunty free non-free
# MySQL Workbench
deb ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/ binary/
deb-src ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/ source/
# Depot PlayOnLinux
deb http://deb.playonlinux.com/ jaunty main
# Ubuntu tweak
deb http://ppa.launchpad.net/tualatrix/ubuntu jaunty main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu jaunty main
##Themes du ZgegBlog: Project Bisigi
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main
john@laptop:~$ 

[/HTML]

System>Administration>Synaptic Package Manager>Settings tab>Repositories>Third Party  uncheck the pppa.launchpad

---

### Post by TSWMIN85 on 2009-07-01
Uncheck all of the ones that say ppa.launchpad?

And out of curiousity, why?

---

### Post by colau on 2009-07-01
> **TSWMIN85 said:**
> Uncheck all of the ones that say ppa.launchpad?

And out of curiousity, why?
```

sudo apt-get update

```
Post the result.

---

### Post by TSWMIN85 on 2009-07-01
Here you go:

> Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_US                     
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1308B]                              
Ign [http://dl.google.com](http://dl.google.com) stable Release                                        
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) jaunty Release.gpg                              
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) jaunty/main Translation-en_US                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-proposed Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-proposed/main Translation-en_US          
Get:3 [http://deb.playonlinux.com](http://deb.playonlinux.com) jaunty Release [1723B]                        
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US              
Get:5 [http://deb.opera.com](http://deb.opera.com) lenny Release.gpg [189B]                            
Ign [http://deb.opera.com](http://deb.opera.com) lenny/non-free Translation-en_US                      
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) jaunty/main Packages                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-proposed/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-proposed/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-proposed/multiverse Translation-en_US    
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-backports Release.gpg                  
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) jaunty/main Packages                            
Get:7 [http://deb.opera.com](http://deb.opera.com) lenny Release [1068B]                               
Ign [http://deb.opera.com](http://deb.opera.com) lenny Release                                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-proposed Release                         
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Get:11 [http://dl.google.com](http://dl.google.com) stable/non-free Packages [954B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty-backports/partner Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-updates Release.gpg                    
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty-updates/partner Translation-en_US      
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-security Release.gpg                   
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty-security/partner Translation-en_US     
Ign [http://deb.opera.com](http://deb.opera.com) lenny/non-free Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:12 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:13 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-proposed Release.gpg                   
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty-proposed/partner Translation-en_US     
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-proposed/main Packages                   
Hit [http://deb.opera.com](http://deb.opera.com) lenny/non-free Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-backports Release                      
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-updates Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-security Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-proposed/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-proposed/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-proposed/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-proposed/main Sources                    
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [52.9kB]                        
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-proposed Release                       
Get:15 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-proposed/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-proposed/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-proposed/multiverse Sources              
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Get:17 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [52.9kB]                        
Get:18 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Get:19 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]                        
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Get:20 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.7kB]                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty-backports/partner Packages             
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty-backports/partner Sources              
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty-updates/partner Packages               
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty-updates/partner Sources                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                               
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty-security/partner Packages              
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty-security/partner Sources               
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty-proposed/partner Packages              
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty-proposed/partner Sources               
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                        
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-backports/partner Packages             
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-backports/partner Sources              
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-updates/partner Packages               
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-updates/partner Sources                
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-security/partner Packages              
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-security/partner Sources               
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-proposed/partner Packages              
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-proposed/partner Sources               
Get:21 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg [197B]                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US            
Get:22 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release [11.7kB]                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                               
Ign [http://download.skype.com](http://download.skype.com) stable Release.gpg                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages      
Ign [http://download.skype.com](http://download.skype.com) stable/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages  
Ign [http://download.skype.com](http://download.skype.com) stable Release                
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty Release.gpg
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty/universe Translation-en_US
Hit [http://download.skype.com](http://download.skype.com) stable/non-free Packages
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-backports Release.gpg
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-backports/main Translation-en_US
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-backports/restricted Translation-en_US
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-backports/universe Translation-en_US
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-backports/multiverse Translation-en_US
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-security Release.gpg
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty Release
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-backports Release
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-updates Release
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-security Release   
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty/main Packages      
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty/universe Packages
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty/main Sources
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty/universe Sources
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-backports/main Packages
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-backports/restricted Packages
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-backports/universe Packages
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-backports/multiverse Packages
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-backports/main Sources
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-backports/restricted Sources
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-backports/universe Sources
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-backports/multiverse Sources
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-security/main Packages
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-security/restricted Packages
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-security/universe Packages
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-security/main Sources
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-security/restricted Sources
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-security/universe Sources
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) jaunty-security/multiverse Sources
Get:23 [ftp://ftp.mysql.com](ftp://ftp.mysql.com) binary/ Release.gpg                                 
Ign [ftp://ftp.mysql.com](ftp://ftp.mysql.com) binary/ Release.gpg                                    
Get:24 [ftp://ftp.mysql.com](ftp://ftp.mysql.com) binary/ Translation-en_US                           
Ign [ftp://ftp.mysql.com](ftp://ftp.mysql.com) binary/ Translation-en_US                              
Get:25 [ftp://ftp.mysql.com](ftp://ftp.mysql.com) source/ Release.gpg                                 
Ign [ftp://ftp.mysql.com](ftp://ftp.mysql.com) source/ Release.gpg                                    
Get:26 [ftp://ftp.mysql.com](ftp://ftp.mysql.com) binary/ Release
Ign [ftp://ftp.mysql.com](ftp://ftp.mysql.com) binary/ Release
Get:27 [ftp://ftp.mysql.com](ftp://ftp.mysql.com) source/ Release
Ign [ftp://ftp.mysql.com](ftp://ftp.mysql.com) source/ Release
Get:28 [ftp://ftp.mysql.com](ftp://ftp.mysql.com) binary/ Packages
Ign [ftp://ftp.mysql.com](ftp://ftp.mysql.com) binary/ Packages
Get:29 [ftp://ftp.mysql.com](ftp://ftp.mysql.com) source/ Sources
Ign [ftp://ftp.mysql.com](ftp://ftp.mysql.com) source/ Sources
Hit [ftp://ftp.mysql.com](ftp://ftp.mysql.com) binary/ Packages
Hit [ftp://ftp.mysql.com](ftp://ftp.mysql.com) source/ Sources
Fetched 4996B in 17s (292B/s)
Reading package lists... Done
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: [http://deb.opera.com](http://deb.opera.com) lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAA
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems


---

### Post by jimv on 2009-07-01
No no no, you don't need to uncheck anything.  You need to add the keys that those repositories are signed with.

Here's a big long command to do that.  Just copy and paste it into your terminal:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A040830F7FAC5991 && sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783 && sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 033431536A423791 && sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 7889D725DA6DEEAA && sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 632D16BB0C713DA6 && sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 28A8205077558DD0 && sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2ED6BB6042C24D89 && sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6AF0E1940624A220 && sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E871C4A881574DE && sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EF4186FE247510BE
```

---

### Post by TSWMIN85 on 2009-07-01
Would I use that same command if I ever run into this problem again?

If not, do you know how I could prevent this in the future.

---

### Post by jimv on 2009-07-01
Generally you use this command:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys
```

And tack the key id on the end.

(The bolded part: 

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY **2EBC26B60C5A2783**)

This doesn't cause any problems, btw...it just means that apt-get can't authenticate that the packages are coming from who they say they are coming from.

---

### Post by colau on 2009-07-01
Yes,no need to remove you have to add those keys.
For medibuntu
```

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by TSWMIN85 on 2009-07-01
You are the man, my friend. You are more of a man than... "place you're preferred celebrity name here."

Thanks, a million.

---

### Post by colau on 2009-07-01
> **TSWMIN85 said:**
> Would I use that same command if I ever run into this problem again?

If not, do you know how I could prevent this in the future.
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys **********

```
At the end of the line replace the * with the key you got in the warning message.

---

### Post by TSWMIN85 on 2009-07-01
Wait, if medibuntu repositories don't come with Ubuntu that means I've installed them myself, right?

The command I just ran gave me the keys to medibuntu, correct?

Another thing, where can I find a thread to give me the run down about repositories?

---

### Post by theozzlives on 2009-07-01
The repositories is just a vast collection of software to choose from. I get the key before I add the source, if they don't have a key I don't install the software.

---

