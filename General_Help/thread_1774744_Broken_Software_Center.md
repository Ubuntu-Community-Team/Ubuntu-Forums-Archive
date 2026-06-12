---
title: "Broken Software Center?"
date: 2011-06-03
forum: General Help
---

### Post by zanzibarwinds on 2011-06-03
Hi

As of today I can't seem to install any packages via the Ubuntu Software Center.

Whenever I click install on anything I get the message "Failed to download package file. Check your Internet connection" and then a second window saying "Requires installation of untrusted packages. The action would require the installation of packages from not authenticated sources."

I tried this for GIMP via the Software Center first and when it failed I installed GIMP through apt-get install gimp without problem.

Now I'm a total new guy to Linux, this Ubuntu instllatiom is only about a week old but this issue is more than likely down to me installing numerous Eclipse addons (Thats the only thing I can think to cause this).

Is there any way I can fix the repo list or whatever it is that could cause this please?

Many thanks for any help any one can give

John

---

### Post by matt_symes on 2011-06-03
Hi

Open a terminal and type

```
sudo apt-get update
```

Please post the resultant text back here between code tags like this.

[noparse]```
 text 
```[/noparse]

Kind regards

---

### Post by zanzibarwinds on 2011-06-04
Hi Matt

Herewith as requested.

Last night I also tried to install Mono Develop, it failed a few times via the Software Center again. I then went into the doftware sources and changed from Main server to South African Server and back again and it seemed to work fine after that.

```

Ign http://za.archive.ubuntu.com natty InRelease                               
Ign http://za.archive.ubuntu.com natty-updates InRelease            
Ign http://za.archive.ubuntu.com natty-security InRelease           
Ign http://archive.canonical.com natty InRelease                    
Hit http://za.archive.ubuntu.com natty Release.gpg
Hit http://za.archive.ubuntu.com natty-updates Release.gpg           
Hit http://za.archive.ubuntu.com natty-security Release.gpg          
Hit http://za.archive.ubuntu.com natty Release                       
Hit http://archive.canonical.com natty Release.gpg                             
Hit http://za.archive.ubuntu.com natty-updates Release               
Hit http://za.archive.ubuntu.com natty-security Release              
Hit http://archive.canonical.com natty Release                                 
Hit http://za.archive.ubuntu.com natty/main Sources                   
Hit http://za.archive.ubuntu.com natty/restricted Sources            
Hit http://za.archive.ubuntu.com natty/universe Sources              
Hit http://za.archive.ubuntu.com natty/multiverse Sources            
Hit http://za.archive.ubuntu.com natty/main i386 Packages            
Hit http://za.archive.ubuntu.com natty/restricted i386 Packages      
Hit http://za.archive.ubuntu.com natty/universe i386 Packages        
Hit http://za.archive.ubuntu.com natty/multiverse i386 Packages      
Ign http://za.archive.ubuntu.com natty/main TranslationIndex         
Ign http://extras.ubuntu.com natty InRelease                         
Hit http://archive.canonical.com natty/partner i386 Packages         
Ign http://za.archive.ubuntu.com natty/multiverse TranslationIndex
Ign http://za.archive.ubuntu.com natty/restricted TranslationIndex   
Ign http://za.archive.ubuntu.com natty/universe TranslationIndex     
Hit http://za.archive.ubuntu.com natty-updates/main Sources          
Hit http://za.archive.ubuntu.com natty-updates/restricted Sources    
Hit http://za.archive.ubuntu.com natty-updates/universe Sources      
Hit http://za.archive.ubuntu.com natty-updates/multiverse Sources    
Get:1 http://extras.ubuntu.com natty Release.gpg [72 B]              
Hit http://za.archive.ubuntu.com natty-updates/main i386 Packages    
Hit http://za.archive.ubuntu.com natty-updates/restricted i386 Packages
Hit http://za.archive.ubuntu.com natty-updates/universe i386 Packages
Ign http://archive.canonical.com natty/partner TranslationIndex
Hit http://za.archive.ubuntu.com natty-updates/multiverse i386 Packages
Ign http://za.archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://za.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://za.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://za.archive.ubuntu.com natty-updates/universe TranslationIndex
Hit http://za.archive.ubuntu.com natty-security/main Sources         
Hit http://extras.ubuntu.com natty Release                           
Hit http://za.archive.ubuntu.com natty-security/restricted Sources    
Hit http://za.archive.ubuntu.com natty-security/universe Sources      
Hit http://za.archive.ubuntu.com natty-security/multiverse Sources    
Hit http://za.archive.ubuntu.com natty-security/main i386 Packages    
Hit http://za.archive.ubuntu.com natty-security/restricted i386 Packages
Hit http://za.archive.ubuntu.com natty-security/universe i386 Packages
Hit http://za.archive.ubuntu.com natty-security/multiverse i386 Packages
Ign http://za.archive.ubuntu.com natty-security/main TranslationIndex
Ign http://za.archive.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://za.archive.ubuntu.com natty-security/restricted TranslationIndex
Ign http://za.archive.ubuntu.com natty-security/universe TranslationIndex
Hit http://extras.ubuntu.com natty/main Sources                      
Hit http://extras.ubuntu.com natty/main i386 Packages                
Ign http://extras.ubuntu.com natty/main TranslationIndex             
Ign http://archive.canonical.com natty/partner Translation-en_ZA                                                      
Ign http://archive.canonical.com natty/partner Translation-en                                                         
Ign http://extras.ubuntu.com natty/main Translation-en_ZA                                                             
Ign http://extras.ubuntu.com natty/main Translation-en                                                                
Ign http://za.archive.ubuntu.com natty/main Translation-en_ZA                                                         
Ign http://za.archive.ubuntu.com natty/main Translation-en                                                            
Ign http://za.archive.ubuntu.com natty/multiverse Translation-en_ZA                                                   
Ign http://za.archive.ubuntu.com natty/multiverse Translation-en                                                      
Ign http://za.archive.ubuntu.com natty/restricted Translation-en_ZA                                                   
Ign http://za.archive.ubuntu.com natty/restricted Translation-en                                                      
Ign http://za.archive.ubuntu.com natty/universe Translation-en_ZA                                                     
Ign http://za.archive.ubuntu.com natty/universe Translation-en                                                        
Ign http://za.archive.ubuntu.com natty-updates/main Translation-en_ZA                                                 
Ign http://za.archive.ubuntu.com natty-updates/main Translation-en                                                    
Ign http://za.archive.ubuntu.com natty-updates/multiverse Translation-en_ZA                                           
Ign http://za.archive.ubuntu.com natty-updates/multiverse Translation-en                                              
Ign http://za.archive.ubuntu.com natty-updates/restricted Translation-en_ZA                                           
Ign http://za.archive.ubuntu.com natty-updates/restricted Translation-en                                              
Ign http://za.archive.ubuntu.com natty-updates/universe Translation-en_ZA                                             
Ign http://za.archive.ubuntu.com natty-updates/universe Translation-en                                                
Ign http://za.archive.ubuntu.com natty-security/main Translation-en_ZA                                                
Ign http://za.archive.ubuntu.com natty-security/main Translation-en                                                   
Ign http://za.archive.ubuntu.com natty-security/multiverse Translation-en_ZA                                          
Ign http://za.archive.ubuntu.com natty-security/multiverse Translation-en                                             
Ign http://za.archive.ubuntu.com natty-security/restricted Translation-en_ZA                                          
Ign http://za.archive.ubuntu.com natty-security/restricted Translation-en                                             
Ign http://za.archive.ubuntu.com natty-security/universe Translation-en_ZA                                            
Ign http://za.archive.ubuntu.com natty-security/universe Translation-en                                               
Fetched 72 B in 12s (6 B/s)                                                                                           
Reading package lists... Done

```

---

### Post by matt_symes on 2011-06-04
Hi

There is nothing wrong when you manually update the package cache. 

Are you still getting the errors from the software centre ?

If you are, can you take some screen shots of the error messages and post them back here ?

Were the errors you were getting for all and every package you tried to install through the software centre ?

Kind regards

---

### Post by zanzibarwinds on 2011-06-04
Hi Matt

Have installed a few things today without issue. Changing the software source servers seemed to clear the problem for some reason.

If it does occur again though I'll be sure to take a screen of it and bring it here.

Regards and thanks
John

---

