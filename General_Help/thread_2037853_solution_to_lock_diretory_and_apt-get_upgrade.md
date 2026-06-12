---
title: "solution to lock diretory and apt-get upgrade?"
date: 2012-08-05
forum: General Help
---

### Post by rulersk on 2012-08-05
Just installed Ubuntu 12.10 using wubi.
Opened a page saying first 10 things to do right after installation.
Tried to install a few cool lenses.
typed in:  sudo add-apt-repository **ppa:jsevi83/unity** && sudo add-apt-repository **ppa:atareao/lenses** && sudo apt-get update
as told on [http://www.omgubuntu.co.uk/2012/01/10-unity-lenses-scopes](http://www.omgubuntu.co.uk/2012/01/10-unity-lenses-scopes)

first i get errors like:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
so i googled and deleted the lock.
then
  	 	 	 	 	 	   Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                  
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                  
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                  
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                                
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                                
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                                
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                                
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                    
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                    
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease                       
 Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg [198 B]           
 Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release [49.6 kB]             
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal InRelease                                 
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates InRelease                         
 Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main amd64 Packages [14 B]    
 Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release.gpg [198 B]                     
 Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted amd64 Packages [14 B]
 Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe amd64 Packages [14 B]
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                    
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                    
 Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse amd64 Packages [14 B]
 Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages [14 B]     
 Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release.gpg [198 B]             
 Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release [49.6 kB]                      
 Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages [14 B]
 Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages [14 B]
 Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages [14 B]
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en             
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en       
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en       
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en         
 Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release [49.6 kB]              
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                               
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                        
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_US          
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_US    
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_US    
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_US      
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                         
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                               
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                        
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                         
 Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main amd64 Packages [1,133 kB]         
 Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                               
   404  Not Found
 Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                        
   404  Not Found
 Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                         
   404  Not Found
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                        
 Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                               
   404  Not Found
 Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                        
   404  Not Found
 Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                         
   404  Not Found
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                        
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                        
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                        
 Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted amd64 Packages [8,597 B]    
 Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe amd64 Packages [5,352 kB]     
 Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse amd64 Packages [127 kB]     
 Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main i386 Packages [1,133 kB]          
 Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted i386 Packages [8,565 B]     
 Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe i386 Packages [5,361 kB]      
 Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse i386 Packages [129 kB]      
 Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en [652 kB]           
 Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-en [97.1 kB]    
 Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en [2,401 B]    
 Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-en [3,678 kB]     
 Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main amd64 Packages [14 B]     
 Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted amd64 Packages [14 B]
 Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe amd64 Packages [14 B]
 Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse amd64 Packages [14 B]
 Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main i386 Packages [14 B]      
 Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted i386 Packages [14 B]
 Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe i386 Packages [14 B]  
 Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse i386 Packages [14 B]
 Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en [14 B]     
 Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-en [14 B]
 Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en [14 B]
 Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-en [14 B]
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en_US                    
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-en_US              
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en_US              
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-en_US                
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en_US            
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-en_US      
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en_US
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-en_US
 Fetched 17.8 MB in 18min 23s (16.2 kB/s)
 W: Failed to fetch [http://ppa.launchpad.net/atareao/lenses/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/atareao/lenses/ubuntu/dists/quantal/main/source/Sources)  404  Not Found
 

 W: Failed to fetch [http://ppa.launchpad.net/atareao/lenses/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/atareao/lenses/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found
 

 W: Failed to fetch [http://ppa.launchpad.net/atareao/lenses/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/atareao/lenses/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found
 

 W: Failed to fetch [http://ppa.launchpad.net/jsevi83/unity/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/jsevi83/unity/ubuntu/dists/quantal/main/source/Sources)  404  Not Found
 

 W: Failed to fetch [http://ppa.launchpad.net/jsevi83/unity/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/jsevi83/unity/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found
 

 W: Failed to fetch [http://ppa.launchpad.net/jsevi83/unity/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/jsevi83/unity/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found
 

 E: Some index files failed to download. They have been ignored, or old ones used instead.
  

Please help. Been trying since morning. Frustrated to the limits/:(

---

### Post by cortman on 2012-08-05
To fix/understand the lock problem, see [here]("http://cortman.wordpress.com/2012/02/24/unable-to-obtain-lock-for-software-installation/").
For the repositories that have gone 404, you should remove lines relating to them in your sources.list, or go to sources.list.d, and delete the pertinent files.

---

