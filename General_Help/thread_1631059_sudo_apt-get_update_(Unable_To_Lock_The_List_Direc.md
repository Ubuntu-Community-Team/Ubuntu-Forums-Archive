---
title: "sudo apt-get update (Unable To Lock The List Directory)?"
date: 2010-11-26
forum: General Help
---

### Post by slixz85 on 2010-11-26
Hi, I am not able to install anything under software center my sources seem fine they all checked and the install button for programs changed to "use this source" and when i try to use terminal with sudo apt-get update before install i get this message:

slixz@slixz-netbook:~$ sudo apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (2: No such file or directory)
E: Unable to lock the list directory
slixz@slixz-netbook:~$ 


any help greatly appreciated

---

### Post by wet-willy on 2010-11-26
Sure looks like the error one gets when Synaptic is open and you try to use dpkg (apt-get) from command line. Shut down all GUI package management systems before running the apt-get update command. If that does not appear to be the issue, try a reboot. If that does not do anything, empty contents of /var/cache/apt/archives/partial as sudo, open a terminal while nothing else is running and issue command: **sudo dpkg --configure -a**
When prompt returns, try again.

---

### Post by Soul-Sing on 2010-11-26
Indeed a reboot will do mostly or try:

```
killall aptitude && killall apt-get
```

```
sudo rm /var/lib/dpkg/lock
```

```
sudo apt-get update
```

then if there is a failure: ```
sudo dpkg --configure -a
```

---

### Post by slixz85 on 2010-11-26
I have definitely tried rebooting and a new session still a problem. no software management running. is there a log of details i can get and post. i am not sure where to find such a thing.

this is what i just did in terminal after fresh boot

slixz@slixz-netbook:~$ killall aptitude && killall apt-get
aptitude: no process found
slixz@slixz-netbook:~$ sudo rm /var/lib/dpkg/lock
slixz@slixz-netbook:~$ sudo apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (2: No such file or directory)
E: Unable to lock the list directory
slixz@slixz-netbook:~$ sudo dpkg --configure -a
slixz@slixz-netbook:~$ sudo apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (2: No such file or directory)
E: Unable to lock the list directory
slixz@slixz-netbook:~$ 

? I've heard about the double process running but its not i have rebooted alot and tried. anything else maybe?

---

### Post by Soul-Sing on 2010-11-26
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

---

### Post by slixz85 on 2010-11-26
just tried it 

slixz@slixz-netbook:~$ sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
[sudo] password for slixz: 
slixz@slixz-netbook:~$ sudo apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (2: No such file or directory)
E: Unable to lock the list directory
slixz@slixz-netbook:~$ 

hmm...

---

### Post by wet-willy on 2010-11-27
I'm currently using Squeeze, I had a look at the /var/lib/apt/lists/lock file on this one and it's just an empty file. Seeing as your error suggest the file is missing, create it with command: **sudo touch /var/lib/apt/lists/lock**

---

### Post by slixz85 on 2010-11-28
doesnt work gives same message

---

### Post by evil_iggy on 2011-02-13
try this:

sudo rm /var/lib/apt/lists/lock

that worked for me.

---

### Post by Icche Ghuri on 2011-04-13
> **evil_iggy said:**
> try this:

sudo rm /var/lib/apt/lists/lock

that worked for me.

Today I,ve got this problem and this works for me too. Thanks a lot evil_iggy :)

---

### Post by fendijr on 2011-07-29
no one helped me at all. to be frank i consider ubuntu is so  complicated to work with it. hundred of thread forum i have followed the instruction since a month but until now nothing happen except 3 things which is error, error and the last one also error.
mine was upgraded from 10:10 to 11:04, yet everything seem suck! who can helped me?? i don`t think so. too many of my time wasted just because of this. missed my damn crashed win 7 which can`t install anymore!

---

### Post by fendijr on 2011-07-29
> **fendijr said:**
> no one helped me at all. to be frank i consider ubuntu is so  complicated to work with it. hundred of thread forum i have followed the instruction since a month but until now nothing happen except 3 things which is error, error and the last one also error.
mine was upgraded from 10:10 to 11:04, yet everything seem suck! who can helped me?? i don`t think so. too many of my time wasted just because of this. missed my damn crashed win 7 which can`t install anymore!

jimmy@jimmy-Aspire-4925:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for jimmy: 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,351 B]                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Get:3 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,262 B]                 
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                       
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages         
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                      
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                            
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://localhost](http://localhost) natty InRelease
Ign [http://localhost](http://localhost) maverick-backports InRelease
Ign [http://localhost](http://localhost) maverick InRelease
Ign [http://localhost](http://localhost) natty InRelease
Ign [http://localhost](http://localhost) maverick InRelease
Ign [http://localhost](http://localhost) maverick-security InRelease
Ign [http://localhost](http://localhost) maverick-updates InRelease
Ign [http://localhost](http://localhost) maverick-backports InRelease
Ign [http://localhost](http://localhost) natty-proposed InRelease
Ign [http://localhost](http://localhost) natty-backports InRelease
Hit [http://localhost](http://localhost) natty Release.gpg
Hit [http://localhost](http://localhost) maverick-backports Release.gpg
Hit [http://localhost](http://localhost) maverick Release.gpg
Hit [http://localhost](http://localhost) natty Release.gpg
Hit [http://localhost](http://localhost) maverick Release.gpg
Get:4 [http://localhost](http://localhost) maverick-security Release.gpg [198 B]
Hit [http://localhost](http://localhost) maverick-updates Release.gpg
Hit [http://localhost](http://localhost) maverick-backports Release.gpg
Hit [http://localhost](http://localhost) natty-proposed Release.gpg
Hit [http://localhost](http://localhost) natty-backports Release.gpg
Hit [http://localhost](http://localhost) natty Release
Hit [http://localhost](http://localhost) maverick-backports Release 
Hit [http://localhost](http://localhost) maverick Release           
Hit [http://localhost](http://localhost) natty Release              
Hit [http://localhost](http://localhost) maverick Release                                          
Get:5 [http://localhost](http://localhost) maverick-security Release [31.4 kB]                     
Hit [http://localhost](http://localhost) maverick-updates Release
Hit [http://localhost](http://localhost) maverick-backports Release   
Hit [http://localhost](http://localhost) natty-proposed Release     
Hit [http://localhost](http://localhost) natty-backports Release    
Hit [http://localhost](http://localhost) natty/main i386 Packages   
Hit [http://localhost](http://localhost) natty/restricted i386 Packages
Hit [http://localhost](http://localhost) natty/universe i386 Packages
Hit [http://localhost](http://localhost) natty/multiverse i386 Packages
Ign [http://localhost](http://localhost) natty/main TranslationIndex
Ign [http://localhost](http://localhost) natty/multiverse TranslationIndex                         
Ign [http://localhost](http://localhost) natty/restricted TranslationIndex
Ign [http://localhost](http://localhost) natty/universe TranslationIndex
Hit [http://localhost](http://localhost) maverick-backports/main Sources
Hit [http://localhost](http://localhost) maverick-backports/restricted Sources
Hit [http://localhost](http://localhost) maverick-backports/universe Sources
Hit [http://localhost](http://localhost) maverick-backports/multiverse Sources
Hit [http://localhost](http://localhost) maverick-backports/main i386 Packages
Hit [http://localhost](http://localhost) maverick-backports/restricted i386 Packages
Hit [http://localhost](http://localhost) maverick-backports/universe i386 Packages
Hit [http://localhost](http://localhost) maverick-backports/multiverse i386 Packages
Ign [http://localhost](http://localhost) maverick-backports/main TranslationIndex
Ign [http://localhost](http://localhost) maverick-backports/multiverse TranslationIndex
Ign [http://localhost](http://localhost) maverick-backports/restricted TranslationIndex
Ign [http://localhost](http://localhost) maverick-backports/universe TranslationIndex
Hit [http://localhost](http://localhost) maverick/partner Sources
Hit [http://localhost](http://localhost) maverick/partner i386 Packages
Ign [http://localhost](http://localhost) maverick/partner TranslationIndex
Hit [http://localhost](http://localhost) natty/main Sources
Hit [http://localhost](http://localhost) natty/main i386 Packages
Ign [http://localhost](http://localhost) natty/main TranslationIndex
Hit [http://localhost](http://localhost) maverick/universe Sources
Hit [http://localhost](http://localhost) maverick/main Sources
Hit [http://localhost](http://localhost) maverick/multiverse Sources
Hit [http://localhost](http://localhost) maverick/restricted Sources
Hit [http://localhost](http://localhost) maverick/main i386 Packages
Hit [http://localhost](http://localhost) maverick/universe i386 Packages
Hit [http://localhost](http://localhost) maverick/restricted i386 Packages
Hit [http://localhost](http://localhost) maverick/multiverse i386 Packages
Ign [http://localhost](http://localhost) maverick/main TranslationIndex
Ign [http://localhost](http://localhost) maverick/multiverse TranslationIndex
Ign [http://localhost](http://localhost) maverick/restricted TranslationIndex
Ign [http://localhost](http://localhost) maverick/universe TranslationIndex
Get:6 [http://localhost](http://localhost) maverick-security/universe Sources [20.5 kB]
Hit [http://localhost](http://localhost) maverick-security/main Sources                            
Hit [http://localhost](http://localhost) maverick-security/multiverse Sources                      
Hit [http://localhost](http://localhost) maverick-security/restricted Sources                      
Get:7 [http://localhost](http://localhost) maverick-security/universe i386 Packages [77.9 kB]      
Hit [http://localhost](http://localhost) maverick-security/main i386 Packages                      
Hit [http://localhost](http://localhost) maverick-security/multiverse i386 Packages                
Hit [http://localhost](http://localhost) maverick-security/restricted i386 Packages                
Ign [http://localhost](http://localhost) maverick-security/main TranslationIndex                   
Ign [http://localhost](http://localhost) maverick-security/multiverse TranslationIndex             
Ign [http://localhost](http://localhost) maverick-security/restricted TranslationIndex             
Ign [http://localhost](http://localhost) maverick-security/universe TranslationIndex               
Hit [http://localhost](http://localhost) maverick-updates/universe Sources                         
Hit [http://localhost](http://localhost) maverick-updates/main Sources                             
Hit [http://localhost](http://localhost) maverick-updates/multiverse Sources                       
Hit [http://localhost](http://localhost) maverick-updates/restricted Sources                       
Hit [http://localhost](http://localhost) maverick-updates/universe i386 Packages                   
Hit [http://localhost](http://localhost) maverick-updates/main i386 Packages                       
Hit [http://localhost](http://localhost) maverick-updates/multiverse i386 Packages                 
Hit [http://localhost](http://localhost) maverick-updates/restricted i386 Packages                 
Ign [http://localhost](http://localhost) maverick-updates/main TranslationIndex                    
Ign [http://localhost](http://localhost) maverick-updates/multiverse TranslationIndex              
Ign [http://localhost](http://localhost) maverick-updates/restricted TranslationIndex              
Ign [http://localhost](http://localhost) maverick-updates/universe TranslationIndex                
Hit [http://localhost](http://localhost) maverick-backports/universe Sources                       
Hit [http://localhost](http://localhost) maverick-backports/main Sources                           
Hit [http://localhost](http://localhost) maverick-backports/multiverse Sources                     
Hit [http://localhost](http://localhost) maverick-backports/restricted Sources                     
Hit [http://localhost](http://localhost) maverick-backports/universe i386 Packages                 
Hit [http://localhost](http://localhost) maverick-backports/main i386 Packages                     
Hit [http://localhost](http://localhost) maverick-backports/multiverse i386 Packages               
Hit [http://localhost](http://localhost) maverick-backports/restricted i386 Packages               
Ign [http://localhost](http://localhost) maverick-backports/main TranslationIndex                  
Ign [http://localhost](http://localhost) maverick-backports/multiverse TranslationIndex            
Ign [http://localhost](http://localhost) maverick-backports/restricted TranslationIndex            
Ign [http://localhost](http://localhost) maverick-backports/universe TranslationIndex              
Hit [http://localhost](http://localhost) natty-proposed/restricted i386 Packages                   
Hit [http://localhost](http://localhost) natty-proposed/main i386 Packages                         
Hit [http://localhost](http://localhost) natty-proposed/multiverse i386 Packages                   
Hit [http://localhost](http://localhost) natty-proposed/universe i386 Packages                     
Ign [http://localhost](http://localhost) natty-proposed/main TranslationIndex                      
Ign [http://localhost](http://localhost) natty-proposed/multiverse TranslationIndex
Ign [http://localhost](http://localhost) natty-proposed/restricted TranslationIndex
Ign [http://localhost](http://localhost) natty-proposed/universe TranslationIndex
Hit [http://localhost](http://localhost) natty-backports/restricted i386 Packages
Hit [http://localhost](http://localhost) natty-backports/main i386 Packages
Hit [http://localhost](http://localhost) natty-backports/multiverse i386 Packages
Hit [http://localhost](http://localhost) natty-backports/universe i386 Packages
Ign [http://localhost](http://localhost) natty-backports/main TranslationIndex
Ign [http://localhost](http://localhost) natty-backports/multiverse TranslationIndex
Ign [http://localhost](http://localhost) natty-backports/restricted TranslationIndex
Ign [http://localhost](http://localhost) natty-backports/universe TranslationIndex
Ign [http://localhost](http://localhost) natty/main Translation-en_US
Ign [http://localhost](http://localhost) natty/main Translation-en
Ign [http://localhost](http://localhost) natty/multiverse Translation-en_US
Ign [http://localhost](http://localhost) natty/multiverse Translation-en
Ign [http://localhost](http://localhost) natty/restricted Translation-en_US
Ign [http://localhost](http://localhost) natty/restricted Translation-en
Ign [http://localhost](http://localhost) natty/universe Translation-en_US
Ign [http://localhost](http://localhost) natty/universe Translation-en
Ign [http://localhost](http://localhost) maverick-backports/main Translation-en_US
Ign [http://localhost](http://localhost) maverick-backports/main Translation-en
Ign [http://localhost](http://localhost) maverick-backports/multiverse Translation-en_US
Ign [http://localhost](http://localhost) maverick-backports/multiverse Translation-en
Ign [http://localhost](http://localhost) maverick-backports/restricted Translation-en_US
Ign [http://localhost](http://localhost) maverick-backports/restricted Translation-en
Ign [http://localhost](http://localhost) maverick-backports/universe Translation-en_US
Ign [http://localhost](http://localhost) maverick-backports/universe Translation-en
Ign [http://localhost](http://localhost) maverick/partner Translation-en_US
Ign [http://localhost](http://localhost) maverick/partner Translation-en
Ign [http://localhost](http://localhost) natty/main Translation-en_US
Ign [http://localhost](http://localhost) natty/main Translation-en
Ign [http://localhost](http://localhost) maverick/main Translation-en_US
Ign [http://localhost](http://localhost) maverick/main Translation-en
Ign [http://localhost](http://localhost) maverick/multiverse Translation-en_US
Ign [http://localhost](http://localhost) maverick/multiverse Translation-en
Ign [http://localhost](http://localhost) maverick/restricted Translation-en_US
Ign [http://localhost](http://localhost) maverick/restricted Translation-en
Ign [http://localhost](http://localhost) maverick/universe Translation-en_US
Ign [http://localhost](http://localhost) maverick/universe Translation-en
Ign [http://localhost](http://localhost) maverick-security/main Translation-en_US
Ign [http://localhost](http://localhost) maverick-security/main Translation-en
Ign [http://localhost](http://localhost) maverick-security/multiverse Translation-en_US
Ign [http://localhost](http://localhost) maverick-security/multiverse Translation-en
Ign [http://localhost](http://localhost) maverick-security/restricted Translation-en_US
Ign [http://localhost](http://localhost) maverick-security/restricted Translation-en
Ign [http://localhost](http://localhost) maverick-security/universe Translation-en_US
Ign [http://localhost](http://localhost) maverick-security/universe Translation-en
Ign [http://localhost](http://localhost) maverick-updates/main Translation-en_US
Ign [http://localhost](http://localhost) maverick-updates/main Translation-en
Ign [http://localhost](http://localhost) maverick-updates/multiverse Translation-en_US
Ign [http://localhost](http://localhost) maverick-updates/multiverse Translation-en
Ign [http://localhost](http://localhost) maverick-updates/restricted Translation-en_US
Ign [http://localhost](http://localhost) maverick-updates/restricted Translation-en
Ign [http://localhost](http://localhost) maverick-updates/universe Translation-en_US
Ign [http://localhost](http://localhost) maverick-updates/universe Translation-en
Ign [http://localhost](http://localhost) maverick-backports/main Translation-en_US
Ign [http://localhost](http://localhost) maverick-backports/main Translation-en
Ign [http://localhost](http://localhost) maverick-backports/multiverse Translation-en_US
Ign [http://localhost](http://localhost) maverick-backports/multiverse Translation-en
Ign [http://localhost](http://localhost) maverick-backports/restricted Translation-en_US
Ign [http://localhost](http://localhost) maverick-backports/restricted Translation-en
Ign [http://localhost](http://localhost) maverick-backports/universe Translation-en_US
Ign [http://localhost](http://localhost) maverick-backports/universe Translation-en
Ign [http://localhost](http://localhost) natty-proposed/main Translation-en_US
Ign [http://localhost](http://localhost) natty-proposed/main Translation-en
Ign [http://localhost](http://localhost) natty-proposed/multiverse Translation-en_US
Ign [http://localhost](http://localhost) natty-proposed/multiverse Translation-en
Ign [http://localhost](http://localhost) natty-proposed/restricted Translation-en_US
Ign [http://localhost](http://localhost) natty-proposed/restricted Translation-en
Ign [http://localhost](http://localhost) natty-proposed/universe Translation-en_US
Ign [http://localhost](http://localhost) natty-proposed/universe Translation-en
Ign [http://localhost](http://localhost) natty-backports/main Translation-en_US
Ign [http://localhost](http://localhost) natty-backports/main Translation-en
Ign [http://localhost](http://localhost) natty-backports/multiverse Translation-en_US
Ign [http://localhost](http://localhost) natty-backports/multiverse Translation-en
Ign [http://localhost](http://localhost) natty-backports/restricted Translation-en_US
Ign [http://localhost](http://localhost) natty-backports/restricted Translation-en
Ign [http://localhost](http://localhost) natty-backports/universe Translation-en_US
Ign [http://localhost](http://localhost) natty-backports/universe Translation-en
Fetched 133 kB in 23min 23s (95 B/s)
W: Failed to fetch [http://ppa.launchpad.net/gnome-media-player-development/development/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/gnome-media-player-development/development/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/gnome-media-player-development/development/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/gnome-media-player-development/development/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
jimmy@jimmy-Aspire-4925:~$ 


see..?? what other can be use now tell me. :confused::confused::confused:

---

### Post by fendijr on 2011-07-29
W: Failed to fetch [http://localhost:9977/localhost:9977/my.archive.ubuntu.com/ubuntu/dists/maverick-backports/InRelease](http://localhost:9977/localhost:9977/my.archive.ubuntu.com/ubuntu/dists/maverick-backports/InRelease)  

W: Failed to fetch [http://localhost:9977/localhost:9977/archive.canonical.com/ubuntu/dists/maverick/InRelease](http://localhost:9977/localhost:9977/archive.canonical.com/ubuntu/dists/maverick/InRelease)  

W: Failed to fetch [http://localhost:9977/localhost:9977/extras.ubuntu.com/ubuntu/dists/natty/InRelease](http://localhost:9977/localhost:9977/extras.ubuntu.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://localhost:9977/localhost:9977/security.ubuntu.com/ubuntu/dists/maverick-security/InRelease](http://localhost:9977/localhost:9977/security.ubuntu.com/ubuntu/dists/maverick-security/InRelease)  

W: Failed to fetch [http://localhost:9977/localhost:9977/archive.ubuntu.com/ubuntu/dists/maverick-updates/InRelease](http://localhost:9977/localhost:9977/archive.ubuntu.com/ubuntu/dists/maverick-updates/InRelease)  

W: Failed to fetch [http://localhost:9977/localhost:9977/archive.ubuntu.com/ubuntu/dists/maverick-backports/InRelease](http://localhost:9977/localhost:9977/archive.ubuntu.com/ubuntu/dists/maverick-backports/InRelease)  

W: Failed to fetch [http://localhost:9977/localhost:9977/my.archive.ubuntu.com/ubuntu/dists/maverick-backports/Release.gpg](http://localhost:9977/localhost:9977/my.archive.ubuntu.com/ubuntu/dists/maverick-backports/Release.gpg)  Unable to connect to localhost:9977: [IP: 127.0.0.1 9977]

W: Failed to fetch [http://localhost:9977/localhost:9977/archive.canonical.com/ubuntu/dists/maverick/Release.gpg](http://localhost:9977/localhost:9977/archive.canonical.com/ubuntu/dists/maverick/Release.gpg)  Unable to connect to localhost:9977: [IP: 127.0.0.1 9977]

W: Failed to fetch [http://localhost:9977/localhost:9977/extras.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://localhost:9977/localhost:9977/extras.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to localhost:9977: [IP: 127.0.0.1 9977]

W: Failed to fetch [http://localhost:9977/localhost:9977/security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg](http://localhost:9977/localhost:9977/security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg)  Unable to connect to localhost:9977: [IP: 127.0.0.1 9977]

W: Failed to fetch [http://localhost:9977/localhost:9977/archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg](http://localhost:9977/localhost:9977/archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg)  Unable to connect to localhost:9977: [IP: 127.0.0.1 9977]

W: Failed to fetch [http://localhost:9977/localhost:9977/archive.ubuntu.com/ubuntu/dists/maverick-backports/Release.gpg](http://localhost:9977/localhost:9977/archive.ubuntu.com/ubuntu/dists/maverick-backports/Release.gpg)  Unable to connect to localhost:9977: [IP: 127.0.0.1 9977]

W: Failed to fetch [http://ppa.launchpad.net/gnome-media-player-development/development/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/gnome-media-player-development/development/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/gnome-media-player-development/development/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/gnome-media-player-development/development/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

W: Some index files failed to download. They have been ignored, or old ones used instead.



AND NOW WHAT IS THIS ALL ABOUT??

---

### Post by elfuego on 2012-06-27
The signatures of today's update could not be verified, so after the update I started googling and ended up here:

[http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/](http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/)

Now, ever since I did this:

```
sudo rm -r /var/lib/apt/*
```

I cannot update apt-get any more. And that's how I ended up in this thread. I keep getting 

```

E: Could not open lock file /var/lib/apt/lists/lock - open (2: No such file or directory)
E: Unable to lock the list directory

```
after executing sudo apt-get update. Synaptic gives the same error. Basically the same problem the thread starter had. Did anyone find a way of fixing this?

---

### Post by nipunshakya on 2012-06-27
there are some solutions in following link... worked for some, didn't for some.... even though, worth trying:
[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/95820](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/95820)
focus on post # 15 and # 16

Goodluck

---

### Post by oldos2er on 2012-06-27
Old thread closed.

Any concerns or questions should be posted in a new thread.

---

