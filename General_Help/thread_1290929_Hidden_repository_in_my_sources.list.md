---
title: "Hidden repository in my sources.list"
date: 2009-10-14
forum: General Help
---

### Post by xenogia on 2009-10-14
I seem to have a hidden repository from playdeb (i think) that gives off a 404 error.  On a sidenote I couldn't find it in the sources.list

This is an update from doing sudo apt-get update

```

Hit http://mirror.iprimus.com.au jaunty Release.gpg
Hit http://mirror.iprimus.com.au jaunty/main Translation-en_AU                                                                                                                                                                                                                                                              
Ign http://mirror.iprimus.com.au jaunty/restricted Translation-en_AU                                                                                                                                                                                                                                                        
Ign http://mirror.iprimus.com.au jaunty/universe Translation-en_AU                                                                                                                                                                                                                                                          
Ign http://mirror.iprimus.com.au jaunty/multiverse Translation-en_AU                                                                                                                                                                                                                                                        
Hit http://mirror.iprimus.com.au jaunty-updates Release.gpg                                                                                                                                                                                                                                                                 
Ign http://mirror.iprimus.com.au jaunty-updates/main Translation-en_AU                                                                                                                                                                                                                                                      
Ign http://mirror.iprimus.com.au jaunty-updates/restricted Translation-en_AU                                                                                                                                                                                                                                                
Ign http://mirror.iprimus.com.au jaunty-updates/universe Translation-en_AU                                                                                                                                                                                                                                                  
Hit http://download.virtualbox.org jaunty Release.gpg                                                                                                                                                                                                                                                                       
Ign http://download.virtualbox.org jaunty/non-free Translation-en_AU                                                                                                                                                                                                                            
Ign http://getdeb.masio.com.mx jaunty/ Release.gpg                                                                                                                                                                                                              
Ign http://getdeb.masio.com.mx jaunty/ Translation-en_AU                                                                                                                                                                                                        
Ign http://mirror.iprimus.com.au jaunty-updates/multiverse Translation-en_AU                                                                                                                                                                                    
Hit http://mirror.iprimus.com.au jaunty-security Release.gpg                                                                                                                                                                                                    
Ign http://mirror.iprimus.com.au jaunty-security/main Translation-en_AU                                                                                                                                                                                         
Ign http://mirror.iprimus.com.au jaunty-security/restricted Translation-en_AU                                                                                                                                                                                   
Ign http://mirror.iprimus.com.au jaunty-security/universe Translation-en_AU                                                                                                                                                                                     
Hit http://download.virtualbox.org jaunty Release                                                                                                                                                                                                               
Ign http://mirror.iprimus.com.au jaunty-security/multiverse Translation-en_AU                                                                                                                                                                                   
Ign http://getdeb.masio.com.mx jaunty/ Release                                                                                                                                                                                                                                                                   
Hit http://mirror.iprimus.com.au jaunty-backports Release.gpg                                                                                                                                                                                                                                
Ign http://mirror.iprimus.com.au jaunty-backports/main Translation-en_AU                                                                                                                                                                                                                                                    
Hit http://archive.canonical.com jaunty Release.gpg                                                                                                                                                                                                                                                                         
Ign http://archive.canonical.com jaunty/partner Translation-en_AU                                                                                                                                                                                                                                      
Hit http://packages.medibuntu.org jaunty Release.gpg                                                                                                                                                                                                                             
Ign http://packages.medibuntu.org jaunty/free Translation-en_AU                                                                                                                                                                                                                                        
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_AU                                                                                                                                                                                                                                    
Ign http://mirror.iprimus.com.au jaunty-backports/restricted Translation-en_AU                                                                                                                                                                                                                         
Get:1 http://packages.linuxmint.com gloria Release.gpg [198B]                                                                                                                                                                                                                    
Ign http://packages.linuxmint.com gloria/main Translation-en_AU                                                                                                                                                                                                    
Ign http://packages.linuxmint.com gloria/upstream Translation-en_AU                                                                                                                                                                   
Ign http://packages.linuxmint.com gloria/import Translation-en_AU                                                                                                                                               
Ign http://mirror.iprimus.com.au jaunty-backports/universe Translation-en_AU                                                                                                                                    
Hit http://download.virtualbox.org jaunty/non-free Packages                                                                                                                                                                                                        
Ign http://mirror.iprimus.com.au jaunty-backports/multiverse Translation-en_AU                                                                                                                                                                                     
Ign http://getdeb.masio.com.mx jaunty/ Packages                                                                                                                                                                                              
Hit http://mirror.iprimus.com.au jaunty Release                                                                                                                                                                                              
Hit http://mirror.iprimus.com.au jaunty-updates Release                                                                                                                                                                                                           
Hit http://mirror.iprimus.com.au jaunty-security Release                                                                                                                                                                                                          
Hit http://mirror.iprimus.com.au jaunty-backports Release                                                                                                                                                                                                         
Hit http://mirror.iprimus.com.au jaunty/main Packages                                                                                                                                                                                                             
Hit http://ppa.launchpad.net jaunty Release.gpg                                                                                                                                                                                              
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU                                                                                                                                                                                   
Hit http://ppa.launchpad.net jaunty Release.gpg                                                                                                                                                                 
Hit http://getdeb.masio.com.mx jaunty/ Packages                                                                                                                                                                 
Hit http://mirror.iprimus.com.au jaunty/restricted Packages                                                                                                                                                     
Hit http://archive.canonical.com jaunty Release                                                                                                                                           
Hit http://packages.medibuntu.org jaunty Release                                                                                                                                          
Hit http://mirror.iprimus.com.au jaunty/universe Packages                                                                                                           
Hit http://wine.budgetdedicated.com jaunty Release.gpg                                                                                                                                    
Ign http://wine.budgetdedicated.com jaunty/main Translation-en_AU                                                                                                                         
Hit http://mirror.iprimus.com.au jaunty/multiverse Packages                                                                                                                               
Ign http://packages.linuxmint.com gloria/backport Translation-en_AU                                                                                                                       
Get:2 http://packages.linuxmint.com gloria Release [9193B]                                                                                                                                
Hit http://mirror.iprimus.com.au jaunty-updates/main Packages                                                                                                       
Hit http://mirror.iprimus.com.au jaunty-updates/restricted Packages                                                                                                                            
Hit http://mirror.iprimus.com.au jaunty-updates/universe Packages                                                                                                                              
Hit http://mirror.iprimus.com.au jaunty-updates/multiverse Packages                                                                                                                            
Hit http://mirror.iprimus.com.au jaunty-security/main Packages                                                                                                                                 
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU                                                                                                                                     
Hit http://ppa.launchpad.net jaunty Release.gpg                                                                                                                                                
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU                                                                                                                                     
Hit http://ppa.launchpad.net jaunty Release.gpg                                                                                                                                                
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU                                                                                  
Hit http://ppa.launchpad.net jaunty Release.gpg                                                                                             
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU                                                                                  
Hit http://ppa.launchpad.net jaunty Release.gpg                                                                                             
Hit http://mirror.iprimus.com.au jaunty-security/restricted Packages                                                                                              
Hit http://archive.canonical.com jaunty/partner Packages                                                                                                                                       
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU                                                                                                                                     
Hit http://ppa.launchpad.net jaunty Release.gpg                                                                                                                          
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU                                                                                  
Hit http://mirror.iprimus.com.au jaunty-security/universe Packages                                                                          
Hit http://packages.medibuntu.org jaunty/free Packages                                                                                                                   
Ign http://archive.getdeb.net Gloria-getdeb Release.gpg                                                                                                                  
Ign http://archive.getdeb.net Gloria-getdeb/games Translation-en_AU                                                                                
Hit http://mirror.iprimus.com.au jaunty-security/multiverse Packages                                                                        
Hit http://wine.budgetdedicated.com jaunty Release                                                                                                                       
Hit http://mirror.iprimus.com.au jaunty-backports/main Packages                                                                                                          
Hit http://mirror.iprimus.com.au jaunty-backports/restricted Packages                                                                                                    
Hit http://mirror.iprimus.com.au jaunty-backports/universe Packages                                                                                                      
Hit http://mirror.iprimus.com.au jaunty-backports/multiverse Packages                                                                                                    
Hit http://ppa.launchpad.net jaunty Release.gpg                                                                  
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU                                                       
Hit http://ppa.launchpad.net jaunty Release.gpg                                                                  
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU                                                       
Hit http://ppa.launchpad.net jaunty Release.gpg                                                                  
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU                                 
Hit http://ppa.launchpad.net jaunty Release.gpg                                            
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU                                 
Hit http://packages.medibuntu.org jaunty/non-free Packages                                                       
Ign http://wine.budgetdedicated.com jaunty/main Packages                                                         
Ign http://archive.getdeb.net Gloria-getdeb Release                                        
Ign http://packages.linuxmint.com gloria/main Packages               
Hit http://ppa.launchpad.net jaunty Release.gpg                      
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU                                 
Hit http://ppa.launchpad.net jaunty Release                                                
Hit http://ppa.launchpad.net jaunty Release                                                
Hit http://ppa.launchpad.net jaunty Release                                                                     
Hit http://ppa.launchpad.net jaunty Release                                                                     
Hit http://ppa.launchpad.net jaunty Release                                                
Hit http://ppa.launchpad.net jaunty Release                                                                     
Hit http://wine.budgetdedicated.com jaunty/main Packages                                                        
Ign http://archive.getdeb.net Gloria-getdeb/games Packages                                 
Ign http://packages.linuxmint.com gloria/upstream Packages           
Hit http://ppa.launchpad.net jaunty Release                          
Hit http://ppa.launchpad.net jaunty Release                                               
Hit http://ppa.launchpad.net jaunty Release                                               
Hit http://ppa.launchpad.net jaunty Release                         
Hit http://ppa.launchpad.net jaunty Release                         
Hit http://ppa.launchpad.net jaunty Release                         
Hit http://ppa.launchpad.net jaunty/main Packages                                         
Hit http://ppa.launchpad.net jaunty/main Sources                                          
Ign http://archive.getdeb.net Gloria-getdeb/games Packages                                
Ign http://packages.linuxmint.com gloria/import Packages             
Ign http://packages.linuxmint.com gloria/backport Packages
Hit http://ppa.launchpad.net jaunty/main Packages                    
Hit http://ppa.launchpad.net jaunty/main Packages                    
Hit http://ppa.launchpad.net jaunty/main Sources                     
Hit http://ppa.launchpad.net jaunty/main Packages                    
Hit http://ppa.launchpad.net jaunty/main Sources                     
Ign http://ppa.launchpad.net jaunty/main Packages                    
Hit http://ppa.launchpad.net jaunty/main Packages                    
Err http://archive.getdeb.net Gloria-getdeb/games Packages           
  404 Not Found
Hit http://ppa.launchpad.net jaunty/main Packages                    
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://packages.linuxmint.com gloria/main Packages
Hit http://ppa.launchpad.net jaunty/main Packages                              
Hit http://packages.linuxmint.com gloria/upstream Packages                     
Hit http://packages.linuxmint.com gloria/import Packages 
Hit http://packages.linuxmint.com gloria/backport Packages
Fetched 9391B in 5s (1738B/s)
W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/Gloria-getdeb/games/binary-amd64/Packages  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```And here is the list of my sources.list file

```

## -----------------------
## LINUX MINT REPOSITORIES
## -----------------------

## +++ Linux Mint 7 Gloria (stable) +++
deb http://packages.linuxmint.com/ gloria main upstream import

## +++ Backports (not as stable) +++
deb http://packages.linuxmint.com/ gloria backport

## +++ Community (not as stable) +++
# deb http://packages.linuxmint.com/ gloria community

## +++ Romeo (unstable) +++
# deb http://packages.linuxmint.com/ gloria romeo

## +++ Source Repositories +++
# deb-src http://packages.linuxmint.com/ gloria main upstream import
# deb-src http://packages.linuxmint.com/ gloria community
# deb-src http://packages.linuxmint.com/ gloria backport
# deb-src http://packages.linuxmint.com/ gloria romeo

## -------------------
## UBUNTU REPOSITORIES
## -------------------

## +++ Ubuntu 9.04 Jaunty (stable) +++
deb http://mirror.iprimus.com.au/ubuntu/ jaunty main restricted universe multiverse
deb http://mirror.iprimus.com.au/ubuntu/ jaunty-updates main restricted universe multiverse
deb http://mirror.iprimus.com.au/ubuntu/ jaunty-security main restricted universe multiverse

## +++ Backports & Proposed (not as stable) +++
deb http://mirror.iprimus.com.au/ubuntu/ jaunty-backports main restricted universe multiverse
# deb http://archive.ubuntu.com/ubuntu/ jaunty-proposed main restricted universe multiverse

## +++ Source Repositories +++
# deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe multiverse
# deb-src http://security.ubuntu.com/ubuntu/ jaunty-security main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ jaunty-proposed main restricted universe multiverse

## ------------------
## OTHER REPOSITORIES
## ------------------

## +++ Canonical (stable) +++
deb http://archive.canonical.com/ubuntu/ jaunty partner

## +++ Medibuntu (stable) +++
deb http://packages.medibuntu.org/ jaunty free non-free

deb http://getdeb.masio.com.mx/ jaunty/
# deb http://download.webmin.com/download/repository sarge contrib

# deb http://ppa.launchpad.net/rvm/smplayer/ubuntu Jaunty main
# deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu jaunty main

deb http://ppa.launchpad.net/themuso/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/themuso/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/tualatrix/gloobus/ubuntu jaunty main
deb http://ppa.launchpad.net/thp/gpodder/ubuntu jaunty main
deb-src http://ppa.launchpad.net/thp/gpodder/ubuntu jaunty main

deb http://ppa.launchpad.net/shiki/mediainfo/ubuntu jaunty main 
deb-src http://ppa.launchpad.net/shiki/mediainfo/ubuntu jaunty main 

```As you may seeing I am currently using Mint 7, but either way its Ubuntu none the less.

---

### Post by scorp123 on 2009-10-14
And underneath **/etc/apt/sources.list.d/** ?  No separate "playdeb.list" or something like that?

---

### Post by xenogia on 2009-10-14
Cheers for that, there was an old playdeb.list file there.  Thanks for your help.

---

### Post by scorp123 on 2009-10-14
> **xenogia said:**
>  Thanks for your help. You're welcome.

Now you have a story to tell on the Linux Mint forum .... You've met me. And are still alive ....  :lol:

(Loooong story. ... Never mind ):P )

---

### Post by xenogia on 2009-10-14
Ahh.. I am going back to Karmic once the official release is out :)

---

### Post by scorp123 on 2009-10-14
> **xenogia said:**
> I am going back to Karmic once the official release is out :) Honestly ... I'd wait a little. Even though Ubuntu's testers try their best to find all bugs before a release ... there will always be a few bugs early on. So I'd wait a month or so until the first patches or so are around.

---

