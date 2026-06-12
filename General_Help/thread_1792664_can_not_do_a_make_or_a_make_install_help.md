---
title: "can not do a make or a make install help"
date: 2011-06-28
forum: General Help
---

### Post by leerpsp on 2011-06-28
ok i download the DeSmuMe Emulater for ubuntu i am runing the 11.04 of ubuntu any way this is what i did

cd Desktop/desmume-0.9.7 

then after that this is what i am in

joshua@joshua-Presario-CQ56-Notebook-PC:~/Desktop/desmume-0.9.7$

then i type make and this is what it tills me 
joshua@joshua-Presario-CQ56-Notebook-PC:~/Desktop/desmume-0.9.7$ make
make: *** No targets specified and no makefile found.  Stop.       
so guys can you till me what is going on because i have naver had it do this befor so can you till me what i am doing wrong or what i need to do just to get this installed  and thanks for the help if you guys can help me with this

---

### Post by gandaran on 2011-06-28
did you run './configure' first according to [instructions]("http://wiki.desmume.org/index.php?title=Installing_DeSmuME_from_source_on_Linux")? and build-essential is installed?

---

### Post by leerpsp on 2011-06-28
> **gandaran said:**
> did you run './configure' first according to [instructions]("http://wiki.desmume.org/index.php?title=Installing_DeSmuME_from_source_on_Linux")? and build-essential is installed?
i did but i dont know if i did it like how do i get the build-essential installed useing the terminal

---

### Post by gandaran on 2011-06-28
```

```> **leerpsp said:**
> i did but i dont know if i did it like how do i get the build-essential installed useing the terminal
```
sudo apt-get install build-essential
```
and check if the dependencies mentioned in the instructions are installed too.

---

### Post by oldos2er on 2011-06-28
```
sudo apt-get update && sudo apt-get install build-essential
```

---

### Post by leerpsp on 2011-06-28
> **gandaran said:**
> ```
sudo apt-get install build-essential
```
 ok i did that and this is what it tills me

eading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

this is just a bad day for me

---

### Post by leerpsp on 2011-06-28
> **oldos2er said:**
> ```
sudo apt-get update && sudo apt-get install build-essential
```

joshua@joshua-Presario-CQ56-Notebook-PC:~$ sudo apt-get update && sudo apt-get install build-essential
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease                       
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                             
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg [198 B]            
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg                     
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release [27.2 kB]              
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources [57.2 kB]         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages          
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources [14 B]      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages        
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources [6,102 B]     
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources [649 B]     
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages [146 kB]    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages [14 B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages [20.7 kB]
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US               
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages [2,065 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en         
Fetched 260 kB in 23s (11.1 kB/s)                                              
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

dont know what is going on

---

### Post by gandaran on 2011-06-28
from the instructions
```
sudo apt-get install build-essential autoconf automake libgtk2.0-dev libglu1-mesa-dev libsdl1.2-dev libglade2-dev gettext zlib1g-dev libosmesa6-dev intltool libagg-dev libasound2-dev
```
this should install everything to run desmume on ubuntu.

---

### Post by leerpsp on 2011-06-28
> **gandaran said:**
> from the instructions
```
sudo apt-get install build-essential autoconf automake libgtk2.0-dev libglu1-mesa-dev libsdl1.2-dev libglade2-dev gettext zlib1g-dev libosmesa6-dev intltool libagg-dev libasound2-dev
```this should install everything to run desmume on ubuntu.

it says the same thing as the other does

---

### Post by oldos2er on 2011-06-28
Try ```
sudo rm /var/lib/apt/lists/* -vf
``` then retry ```
sudo apt-get update && sudo apt-get install build-essential
```

---

### Post by leerpsp on 2011-06-28
> **oldos2er said:**
> Try ```
sudo rm /var/lib/apt/lists/* -vf
``` then retry ```
sudo apt-get update && sudo apt-get install build-essential
```

ok i did it and it says that build-essential is already the newest version. and it is now installing new updates for ubuntu and i will see if it will work after it gets done updateing one more thing to ask my ubuntu software center will not work when i go to use and like click on games it will lode for ever and not a thing will come up to download for it can you guys help with that y i am updateing my ubuntu

---

### Post by leerpsp on 2011-06-28
> **oldos2er said:**
> Try ```
sudo rm /var/lib/apt/lists/* -vf
``` then retry ```
sudo apt-get update && sudo apt-get install build-essential
```
the build essential is installed and it is still saying this
make: *** No targets specified and no makefile found.  Stop.

---

### Post by leerpsp on 2011-06-28
ok after i did that and restarted my ubuntu software center started working i may can not install it useing the other way so i fond the Desume on the ubuntu software center and installed it so thank you for you help but i got what i wonted but keep this up so if some one that is haveing the same thing go wrong can get some help with it

---

