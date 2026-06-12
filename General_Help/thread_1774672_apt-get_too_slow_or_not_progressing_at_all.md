---
title: "apt-get too slow or not progressing at all"
date: 2011-06-03
forum: General Help
---

### Post by feddozz on 2011-06-03
The title is self explanatory
Here it is:
[LIST]
[*]My internet connection is ok
[*]i can't install apps or update with update manager
[*]i am using standard repositories, nothing fancy
[*]the installation is pretty sandard
[*]this appened after an update with update manager, i think...
[/LIST]
any ideas?
Tnx

---

### Post by wolfen69 on 2011-06-03
We need more info to help you. What exactly happens when you try to install something?

---

### Post by linuxinstalledfromhdd on 2011-06-03
> **feddozz said:**
> The title is self explanatory
Here it is:
[LIST]
[*]My internet connection is ok
[*]i can't install apps or update with update manager
[*]i am using standard repositories, nothing fancy
[*]the installation is pretty sandard
[*]this appened after an update with update manager, i think...
[/LIST]
any ideas?
Tnx

Try using a hardwired connection to the internet.

---

### Post by feddozz on 2011-06-03
> **linuxinstalledfromhdd said:**
> Try using a hardwired connection to the internet.

??
I am replying to this post with the machine in question, so my network connection is fine. What makes you think that apt works better with a wired connection??

---

### Post by feddozz on 2011-06-03
> **wolfen69 said:**
> We need more info to help you. What exactly happens when you try to install something?

I tried issuing the following command:
```
sudo apt-get update
Ign http://security.ubuntu.com natty-security InRelease
Ign http://archive.canonical.com natty InRelease                    
Ign http://extras.ubuntu.com natty InRelease                         
Hit http://security.ubuntu.com natty-security Release.gpg            
Get:1 http://archive.canonical.com natty Release.gpg [198 B]         
Get:2 http://extras.ubuntu.com natty Release.gpg [72 B]              
Hit http://security.ubuntu.com natty-security Release                
Get:3 http://archive.canonical.com natty Release [5,916 B]                        
Hit http://extras.ubuntu.com natty Release                                        
Hit http://security.ubuntu.com natty-security/main Sources                        
Ign http://gb.archive.ubuntu.com natty InRelease                                  
Ign http://gb.archive.ubuntu.com natty-updates InRelease                
Hit http://extras.ubuntu.com natty/main Sources                         
Hit http://security.ubuntu.com natty-security/restricted Sources     
Hit http://security.ubuntu.com natty-security/universe Sources                    
Hit http://security.ubuntu.com natty-security/multiverse Sources                  
Hit http://security.ubuntu.com natty-security/main i386 Packages                  
Hit http://security.ubuntu.com natty-security/restricted i386 Packages            
Hit http://gb.archive.ubuntu.com natty Release.gpg                                
Get:4 http://archive.canonical.com natty/partner i386 Packages [7,861 B]          
Hit http://security.ubuntu.com natty-security/universe i386 Packages              
Hit http://security.ubuntu.com natty-security/multiverse i386 Packages            
Ign http://security.ubuntu.com natty-security/main TranslationIndex               
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex         
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex         
Hit http://extras.ubuntu.com natty/main i386 Packages                             
Ign http://extras.ubuntu.com natty/main TranslationIndex                          
Hit http://gb.archive.ubuntu.com natty-updates Release.gpg                        
Ign http://security.ubuntu.com natty-security/universe TranslationIndex         
Ign http://archive.canonical.com natty/partner TranslationIndex                   
Hit http://gb.archive.ubuntu.com natty Release                                    
Ign http://extras.ubuntu.com natty/main Translation-en_GB                         
Hit http://gb.archive.ubuntu.com natty-updates Release                            
Ign http://security.ubuntu.com natty-security/main Translation-en_GB              
Ign http://security.ubuntu.com natty-security/main Translation-en                 
Ign http://extras.ubuntu.com natty/main Translation-en                            
Ign http://archive.canonical.com natty/partner Translation-en_GB                  
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_GB        
Ign http://security.ubuntu.com natty-security/multiverse Translation-en           
Ign http://security.ubuntu.com natty-security/restricted Translation-en_GB
Ign http://security.ubuntu.com natty-security/restricted Translation-en
Ign http://security.ubuntu.com natty-security/universe Translation-en_GB
Ign http://archive.canonical.com natty/partner Translation-en         
Ign http://security.ubuntu.com natty-security/universe Translation-en 
Hit http://gb.archive.ubuntu.com natty/main Sources
Hit http://gb.archive.ubuntu.com natty/restricted Sources
Hit http://gb.archive.ubuntu.com natty/universe Sources
Hit http://gb.archive.ubuntu.com natty/multiverse Sources
Hit http://gb.archive.ubuntu.com natty/main i386 Packages
Hit http://gb.archive.ubuntu.com natty/restricted i386 Packages
Hit http://gb.archive.ubuntu.com natty/universe i386 Packages
Hit http://gb.archive.ubuntu.com natty/multiverse i386 Packages
Ign http://gb.archive.ubuntu.com natty/main TranslationIndex
Ign http://gb.archive.ubuntu.com natty/multiverse TranslationIndex
Ign http://gb.archive.ubuntu.com natty/restricted TranslationIndex
Ign http://gb.archive.ubuntu.com natty/universe TranslationIndex
Hit http://gb.archive.ubuntu.com natty-updates/main Sources
Hit http://gb.archive.ubuntu.com natty-updates/restricted Sources
Hit http://gb.archive.ubuntu.com natty-updates/universe Sources
Hit http://gb.archive.ubuntu.com natty-updates/multiverse Sources
Get:5 http://gb.archive.ubuntu.com natty-updates/main i386 Packages [116 kB]
Get:6 http://gb.archive.ubuntu.com natty-updates/main i386 Packages [116 kB]      
Get:7 http://gb.archive.ubuntu.com natty-updates/main i386 Packages [116 kB]      
Get:8 http://gb.archive.ubuntu.com natty-updates/main i386 Packages [116 kB]      
Get:9 http://gb.archive.ubuntu.com natty-updates/main i386 Packages [116 kB]      
Get:10 http://gb.archive.ubuntu.com natty-updates/main i386 Packages [116 kB]     
Get:11 http://gb.archive.ubuntu.com natty-updates/main i386 Packages [116 kB]     
Get:12 http://gb.archive.ubuntu.com natty-updates/main i386 Packages [116 kB]     
Get:13 http://gb.archive.ubuntu.com natty-updates/main i386 Packages [116 kB]     
Get:14 http://gb.archive.ubuntu.com natty-updates/restricted i386 Packages [14 B] 
Get:15 http://gb.archive.ubuntu.com natty-updates/universe i386 Packages [44.0 kB]
Get:16 http://gb.archive.ubuntu.com natty-updates/universe i386 Packages [44.0 kB]
Get:17 http://gb.archive.ubuntu.com natty-updates/universe i386 Packages [44.0 kB]
Get:18 http://gb.archive.ubuntu.com natty-updates/multiverse i386 Packages [3,754 B]
Get:19 http://gb.archive.ubuntu.com natty-updates/multiverse i386 Packages [3,754 B]
Ign http://gb.archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://gb.archive.ubuntu.com natty-updates/multiverse TranslationIndex        
Ign http://gb.archive.ubuntu.com natty-updates/restricted TranslationIndex        
Ign http://gb.archive.ubuntu.com natty-updates/universe TranslationIndex          
Hit http://gb.archive.ubuntu.com natty/main Translation-en_GB                     
Hit http://gb.archive.ubuntu.com natty/multiverse Translation-en_GB               
Hit http://gb.archive.ubuntu.com natty/restricted Translation-en_GB               
Hit http://gb.archive.ubuntu.com natty/universe Translation-en_GB                 
Get:20 http://gb.archive.ubuntu.com natty-updates/universe i386 Packages [44.0 kB]
Get:21 http://gb.archive.ubuntu.com natty-updates/universe i386 Packages [44.0 kB]
Get:22 http://gb.archive.ubuntu.com natty-updates/universe i386 Packages [44.0 kB]
Get:23 http://gb.archive.ubuntu.com natty-updates/universe i386 Packages [44.0 kB]
Err http://gb.archive.ubuntu.com natty-updates/universe i386 Packages             
  404  Not Found
Ign http://gb.archive.ubuntu.com natty/main Translation-en                        
Ign http://gb.archive.ubuntu.com natty/multiverse Translation-en
Ign http://gb.archive.ubuntu.com natty/restricted Translation-en
Ign http://gb.archive.ubuntu.com natty/universe Translation-en
Ign http://gb.archive.ubuntu.com natty-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com natty-updates/main Translation-en
Ign http://gb.archive.ubuntu.com natty-updates/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://gb.archive.ubuntu.com natty-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://gb.archive.ubuntu.com natty-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com natty-updates/universe Translation-en
Fetched 30.5 kB in 50min 54s (10 B/s)
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```
It takes too long, it is very slow and does not find some of the files.

Other example: update manager downloads at .5 B/s!! I just performed a speed test to my broad band and it's all fine.

I also tried to install didrip with apt-get. it doesnot progress the download. it just sits there for too long.

---

