---
title: "need help install k3B"
date: 2009-08-29
forum: General Help
---

### Post by starcraftmaster on 2009-08-29
hey guys
i tried installing K3B and this is what i get(typed sudo **apt-get update; apt-get install k3b**in tirminal)

Hit [http://mirror.optus.net](http://mirror.optus.net) jaunty Release.gpg
Hit [http://mirror.optus.net](http://mirror.optus.net) jaunty/main Translation-en_AU
Ign [http://mirror.optus.net](http://mirror.optus.net) jaunty/restricted Translation-en_AU
Ign [http://mirror.optus.net](http://mirror.optus.net) jaunty/universe Translation-en_AU
Ign [http://mirror.optus.net](http://mirror.optus.net) jaunty/multiverse Translation-en_AU                
Get:1 [http://mirror.optus.net](http://mirror.optus.net) jaunty-updates Release.gpg [189B]                
Ign [http://mirror.optus.net](http://mirror.optus.net) jaunty-updates/main Translation-en_AU              
Ign [http://mirror.optus.net](http://mirror.optus.net) jaunty-updates/restricted Translation-en_AU        
Ign [http://mirror.optus.net](http://mirror.optus.net) jaunty-updates/universe Translation-en_AU          
Ign [http://mirror.optus.net](http://mirror.optus.net) jaunty-updates/multiverse Translation-en_AU        
Get:2 [http://mirror.optus.net](http://mirror.optus.net) jaunty-security Release.gpg [189B]               
Ign [http://mirror.optus.net](http://mirror.optus.net) jaunty-security/main Translation-en_AU             
Ign [http://mirror.optus.net](http://mirror.optus.net) jaunty-security/restricted Translation-en_AU       
Ign [http://mirror.optus.net](http://mirror.optus.net) jaunty-security/universe Translation-en_AU         
Ign [http://mirror.optus.net](http://mirror.optus.net) jaunty-security/multiverse Translation-en_AU       
Hit [http://mirror.optus.net](http://mirror.optus.net) jaunty Release                                     
Get:3 [http://mirror.optus.net](http://mirror.optus.net) jaunty-updates Release [49.6kB]                  
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_AU              
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Get:4 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release.gpg [191B]
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Translation-en_AU        
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                  
Get:5 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release [1019B]
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages
Get:6 [http://mirror.optus.net](http://mirror.optus.net) jaunty-security Release [49.6kB]                 
Hit [http://mirror.optus.net](http://mirror.optus.net) jaunty/main Packages                               
Hit [http://mirror.optus.net](http://mirror.optus.net) jaunty/restricted Packages                         
Hit [http://mirror.optus.net](http://mirror.optus.net) jaunty/universe Packages                           
Hit [http://mirror.optus.net](http://mirror.optus.net) jaunty/multiverse Packages                         
Get:7 [http://mirror.optus.net](http://mirror.optus.net) jaunty-updates/main Packages [160kB]             
Get:8 [http://mirror.optus.net](http://mirror.optus.net) jaunty-updates/restricted Packages [2589B]       
Get:9 [http://mirror.optus.net](http://mirror.optus.net) jaunty-updates/universe Packages [54.0kB]        
Get:10 [http://mirror.optus.net](http://mirror.optus.net) jaunty-updates/multiverse Packages [6637B]      
Get:11 [http://mirror.optus.net](http://mirror.optus.net) jaunty-security/main Packages [87.4kB]          
Get:12 [http://mirror.optus.net](http://mirror.optus.net) jaunty-security/restricted Packages [2589B]     
Get:13 [http://mirror.optus.net](http://mirror.optus.net) jaunty-security/universe Packages [34.2kB]      
Get:14 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages [1271B]            
Get:15 [http://mirror.optus.net](http://mirror.optus.net) jaunty-security/multiverse Packages [1662B]     
Fetched 451kB in 1min 16s (5901B/s)                                            
Reading package lists... Done
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by chriskin on 2009-08-29
try sudo apt-get install k3b

---

### Post by starcraftmaster on 2009-09-01
yer it worked great
thanks mate

---

