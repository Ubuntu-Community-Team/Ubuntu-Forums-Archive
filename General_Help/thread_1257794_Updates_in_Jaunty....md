---
title: "Updates in Jaunty..."
date: 2009-09-04
forum: General Help
---

### Post by pgfan92 on 2009-09-04
I get a message every time I update:  E: Some index files failed to download, they have been ignored, or old ones used instead.

I put in a command: sudo apt-get update

Here's what happened:

adam@adam-desktop:~$ sudo apt-get update
[sudo] password for adam: 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty Release.gpg                            
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/main Translation-en_US                 
Hit [http://wine.budgetdedicated.com]("http://wine.budgetdedicated.com/") edgy Release.gpg                
Ign [http://wine.budgetdedicated.com]("http://wine.budgetdedicated.com/") edgy/main Translation-en_US                
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/main Translation-en_US          
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/restricted Translation-en_US    
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty Release.gpg                           
Ign [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty/free Translation-en_US                
Ign [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty/non-free Translation-en_US            
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/multiverse Translation-en_US           
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates Release.gpg                    
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-backports Release.gpg        
Hit [http://wine.budgetdedicated.com]("http://wine.budgetdedicated.com/") edgy Release                               
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-backports/main Translation-en_US       
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security Release               
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty Release                               
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-backports/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-backports/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-backports/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") edgy Release.gpg                              
Ign [http://wine.budgetdedicated.com]("http://wine.budgetdedicated.com/") edgy/main Packages                         
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/main Packages                   
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") edgy/universe Translation-en_US     
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty Release                      
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates Release              
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty/free Packages                         
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-backports Release                      
Hit [http://wine.budgetdedicated.com]("http://wine.budgetdedicated.com/") edgy/main Packages                         
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/restricted Packages             
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/main Sources          
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/restricted Sources    
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/universe Packages     
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") jaunty/non-free Packages           
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") edgy Release                        
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/main Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/main Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/universe Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/universe Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/universe Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-backports/main Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-backports/restricted Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-backports/universe Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") jaunty-backports/multiverse Packages
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") edgy/universe Packages
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") edgy/universe Packages
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") edgy/universe Packages
  404 Not Found [IP: 91.189.88.45 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.88.45 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

What do I do to make the message go away?

---

### Post by credobyte on 2009-09-04
```
sudo gedit /etc/apt/sources.list
```

```
Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") [COLOR=Red]**edgy**[/COLOR]/universe Packages
```

Remove all edgy links from the end of your file & you should be fine :)

---

### Post by pgfan92 on 2009-09-04
Thanks..I'm kinda new to this whole Ubuntu thing...

---

