---
title: "Software center not working"
date: 2011-10-07
forum: General Help
---

### Post by Urbanblaze on 2011-10-07
It's not loading properly. I can open it, but thats about all. nothing else. 
Anything I can try to fix it? :)

---

### Post by MG&amp;TL on 2011-10-07
Run:

```
software-center
```

In a terminal, and post what happens. You might be missing a library or whatever. Do all the other package managers work?

---

### Post by Urbanblaze on 2011-10-07
nothing happens when I do that. Just goes back down to tiara blah blah blah. doesnt do the pword thing :/

---

### Post by MG&amp;TL on 2011-10-07
Something should happen. The software centre should open, then try to click and see what happens in the terminal. If nothing, file a bug in launchpad: [https://bugs.launchpad.net/](https://bugs.launchpad.net/) and it will get fixed of you provide enough information

---

### Post by matt_symes on 2011-10-07
Hi

Let's try this first. Open a terminal and type

```
sudo apt-get update
```

Post the results back here by copy and pasting the results between code tags.

Kind regards

---

### Post by MG&amp;TL on 2011-10-07
+1, I assumed he meant that nothing happened when he clicked the buttons.

Tiara thing?

---

### Post by Urbanblaze on 2011-10-07
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                       
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg [198 B]  
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                           
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release [31.4 kB]    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                           
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg [198 B]           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex             
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release [31.4 kB]   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources [71.1 kB]         
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
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources [14 B]      
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources [11.3 kB]     
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources [657 B]     
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages [191 kB]   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex               
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources [134 kB]        
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages [14 B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages [42.5 kB]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages [2,077 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources [753 B]   
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources [28.2 kB]   
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources [1,888 B] 
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages [388 kB]  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages [839 B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages [106 kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages [4,614 B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en         
Fetched 1,046 kB in 6s (152 kB/s)                                              
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
 for the most recent sudo command

---

### Post by matt_symes on 2011-10-07
Hi

Open a terminal and type

```
sudo rm -rf  /var/lib/apt/lists/*
```

Enter your password. It will not be echoed to the screen.

Then type

```
sudo apt-get update
```

When that has finished open software centre (or synaptic) again.

Kind regards

---

### Post by Urbanblaze on 2011-10-07
okay. so i open the terminal. put the first. hit enter. the put my password. and It doesnt show on the screen at all like u said. hit enter then put the second??

---

### Post by MG&amp;TL on 2011-10-07
Yeah. Any commands people tell you to enter are designed to be typed in their entireity, then ENTER-ed. You are then asked to follow any prompts (and then ENTER them!) the program or script gives you.

Subsequent commands are then entered separately like the first.

For more information, try [http://Linuxcommand.org]("http://Linuxcommand.org")

---

### Post by matt_symes on 2011-10-07
Hi

Somehow you misunderstood me.

Open a terminal and type

     ```
sudo rm -rf  /var/lib/apt/lists/*
```Type in your password. It will not be echoed to the screen. Then hit <enter>.

Then type

```
sudo apt-get update
```Kind regards

---

### Post by Urbanblaze on 2011-10-07
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                         
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg [316 B]             
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]                        
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg [198 B]            
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release [9,736 B]                         
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release [9,753 B]                         
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release [31.4 kB]              
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources [834 B]                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease                       
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages [2,822 B]              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg [198 B]                   
Get:10 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources [14 B]                      
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources [71.1 kB]        
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg [198 B]          
Get:13 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages [14 B]                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release [39.8 kB]                    
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources [14 B]     
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources [11.3 kB]    
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources [657 B]    
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages [191 kB]   
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release [31.4 kB]            
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages [14 B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages [42.5 kB]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages [2,077 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources [862 kB]                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources [4,104 B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources [4,380 kB]        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en          
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources [155 kB]                                                                                                  
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages [1,550 kB]                                                                                                
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages [8,986 B]                                                                                           
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages [6,021 kB]                                                                                            
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages [183 kB]                                                                                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                                                                                                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex                                                                                                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex                                                                                                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex                                                                                                       
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources [134 kB]                                                                                                
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources [753 B]                                                                                           
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources [28.2 kB]                                                                                           
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources [1,888 B]                                                                                         
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages [388 kB]                                                                                          
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages [839 B]                                                                                     
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages [106 kB]                                                                                      
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages [4,614 B]                                                                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex                                                                                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex                                                                                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex                                                                                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex                                                                                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US                                                                                                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en                                                                                                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US                                                                                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en                                                                                                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US                                                                                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en                                                                                                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US                                                                                                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en                                                                                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US                                                                                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en                                                                                                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US                                                                                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en                                                                                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US                                                                                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en                                                                                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US                                                                                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en                                                                                                 
Fetched 14.3 MB in 32s (444 kB/s)                                                                                                                                      
Reading package lists... Done


should it b fine now?

---

### Post by matt_symes on 2011-10-07
Hi

> should it b fine now?Yes :D

If it's not then post back. If it is then mark this thread as solved.

Kind regards

---

