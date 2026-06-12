---
title: "Connection drops whenever I try to update repositories"
date: 2011-05-12
forum: General Help
---

### Post by 3 frags left on 2011-05-12
Something really fu&#1089;ked-up is going on with my machine... whenever I try to update my repositories (regardless of if it's by Synaptic, Ubuntu Software Center or terminal via *sudo apt-get update*), my PC loses connection, and I need to reset my WLAN twice to make it work. It's in a specific part where it happens...
```
Ign http://archive.ubuntu.com natty InRelease                                  
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                        
Ign http://archive.canonical.com natty InRelease                    
Hit http://ppa.launchpad.net natty Release.gpg                       
Ign http://archive.ubuntu.com natty-updates InRelease                
Hit http://archive.canonical.com natty Release.gpg                   
Hit http://ppa.launchpad.net natty Release                           
Ign http://archive.ubuntu.com natty-security InRelease               
Hit http://archive.canonical.com natty Release                                 
Get:1 http://archive.ubuntu.com natty Release.gpg [198 B]                      
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://archive.canonical.com natty/partner i386 Packages                   
Hit http://extras.ubuntu.com natty Release.gpg                       
Hit http://ppa.launchpad.net natty/main i386 Packages                
Ign http://archive.canonical.com natty/partner TranslationIndex                
Get:2 http://archive.ubuntu.com natty-updates Release.gpg [198 B]              
Hit http://extras.ubuntu.com natty Release                                     
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://extras.ubuntu.com natty/main Sources                      
Get:3 http://archive.ubuntu.com natty-security Release.gpg [198 B]   
Hit http://extras.ubuntu.com natty/main i386 Packages                          
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Get:4 http://archive.ubuntu.com natty Release [39.8 kB]                        
Get:5 http://archive.ubuntu.com natty-updates Release [27.2 kB]                
Err http://extras.ubuntu.com natty/main Translation-en_US                      
  Unable to connect to extras.ubuntu.com:http:
Err http://extras.ubuntu.com natty/main Translation-en                         
  Unable to connect to extras.ubuntu.com:http:
Err http://archive.canonical.com natty/partner Translation-en_US               
  Unable to connect to archive.canonical.com:http:
Err http://ppa.launchpad.net natty/main Translation-en_US                      
  Unable to connect to ppa.launchpad.net:http:
Err http://archive.canonical.com natty/partner Translation-en                  
  Unable to connect to archive.canonical.com:http:
Err http://ppa.launchpad.net natty/main Translation-en
  Unable to connect to ppa.launchpad.net:http:
63% [5 Release 2,491 B/27.2 kB 9%]
```
Special attention to the last lines. Measures I've tried:

[LIST]
[*]Remove every package I installed today (the problem started today)
[*]Removed the repositories I've inserted.
[*]Rebooted the PC several times (rebooting does not help)
[/LIST]

Any help, gentlemen?

Edit: Being more specific... when it gets here:
```
Get:5 http://archive.ubuntu.com natty-updates Release [27.2 kB]                
Err http://extras.ubuntu.com natty/main Translation-en_US
```
my connection is lost. Exactly at this point. Wonder if the problem isn't @ Canonical?

---

### Post by 3 frags left on 2011-05-12
Bumping is not polite, but I'm really in need for help. Sorry.

---

### Post by plucky on 2011-05-12
> **3 frags left said:**
> Bumping is not polite, but I'm really in need for help. Sorry.

Swearing is also not appreciated and don't be surprised if a Mod doesn't edit your post.

Have you tried a different server?

Try connecting using a wired connection and see if that makes a difference.

Do you lose the connection when downloading the Ubuntu ISO?

You could try disabling all the repositories and then just adding each one back again and see if one fails.

Also post your sources.list with ```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d/
```

---

