---
title: "Error when compiling RadioCountTo Leds"
date: 2012-06-21
forum: General Help
---

### Post by Narjess on 2012-06-21
Hi All, 
I'm new here, and I have several problems with Ubuntu;

when I compile the RadioCountTo Leds, I receive an error message that ends like that :  
RadioCountToLeds.h:34: syntax error before `nx_uint16_t' 
RadioCountToLeds.h:34: warning: no semicolon at end of struct or union 
RadioCountToLeds.h:35: warning: data definition has no type or storage class failed to parse message file RadioCountToLeds.h 
make: *** [RadioCountMsg.py] Error 1  

An other problem is when I type : sudo apt&#8208;get &#8233;install &#8233;build&#8208;essential
I have the ' sudo: apt&#8208;get: command not found ' error

Can any one help me please :( thanks

---

### Post by raja.genupula on 2012-06-21
open synaptic manager and search for apt-get . if its not installed , install it and try again .

---

### Post by Narjess on 2012-06-21
But apt-get works otherwise such as when I execute : 

$ sudo apt-get update && sudo apt-get upgrade


and for the first problem, did you have any idea please ?

---

### Post by raja.genupula on 2012-06-21
> **Narjess said:**
> But apt-get works otherwise such as when I execute : 

$ sudo apt-get update && sudo apt-get upgrade


and for the first problem, did you have any idea please ?


copy and paste the terminal code what you've entered and you got .

---

### Post by Narjess on 2012-06-21
I had the same problem :(

narjess@narjess-Satellite-L505D:/etc/apt$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for narjess: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                                       
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                                                
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en                     
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en                         
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en                                
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US                  
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US                      
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US                             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en               
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                                    
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US            
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en               
Ign [http://hinrg.cs.jhu.edu](http://hinrg.cs.jhu.edu) maverick Release.gpg                                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                                               
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US            
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                                         
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en                 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release             
Ign [http://hinrg.cs.jhu.edu/tinyos/](http://hinrg.cs.jhu.edu/tinyos/) maverick/main Translation-en                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages                  
Ign [http://hinrg.cs.jhu.edu/tinyos/](http://hinrg.cs.jhu.edu/tinyos/) maverick/main Translation-en_US                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages                  
Hit [http://hinrg.cs.jhu.edu](http://hinrg.cs.jhu.edu) maverick Release                                               
Ign [http://hinrg.cs.jhu.edu](http://hinrg.cs.jhu.edu) maverick/main i386 Packages/DiffIndex    
Ign [http://hinrg.cs.jhu.edu](http://hinrg.cs.jhu.edu) maverick/main i386 Packages
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick Release.gpg
Ign [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Ign [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
Ign [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates Release.gpg
Ign [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Ign [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/) maverick/main Translation-en
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick Release                    
Ign [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/) maverick/main Translation-en_US   
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates Release                                  
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/main Sources                                     
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/restricted Sources         
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/universe Sources
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/multiverse Sources         
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/main i386 Packages         
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/restricted i386 Packages   
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]           
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/universe i386 Packages              
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/multiverse i386 Packages   
Ign [http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu/](http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu/) maverick/main Translation-en
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/main Sources       
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/restricted Sources
Ign [http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu/](http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu/) maverick/main Translation-en_US
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/universe Sources
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release [9,752B]             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                                
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/multiverse Sources                         
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release [9,762B]             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                          
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/main i386 Packages   
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages/DiffIndex   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources/DiffIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages/DiffIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Ign [http://hinrg.cs.jhu.edu](http://hinrg.cs.jhu.edu) maverick/main i386 Packages
Hit [http://hinrg.cs.jhu.edu](http://hinrg.cs.jhu.edu) maverick/main i386 Packages
Fetched 634B in 5s (121B/s)
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7274A4DAE80D6BF5
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5BB92C09DB82666C
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
narjess@narjess-Satellite-L505D:/etc/apt$ sudo apt&#8208;get &#8233;install &#8233;build&#8208;essential
sudo: apt&#8208;get: command not found

---

