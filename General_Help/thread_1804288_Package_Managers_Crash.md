---
title: "Package Managers Crash"
date: 2011-07-14
forum: General Help
---

### Post by Gen2ly on 2011-07-14
All my package managers are crashing.  I will try to start them up, they will begin loading, and then will crash.  The problem began with the Update Manager putting up the red circle error icon that says: "An error has occured, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong.  The error message was: 'Error: BrokenCount > 0'.  This usually means that your installed packages have unmet dependencies."

The recommended fix for this looks to be on this post that I got from LaunchPad:

[http://ubuntuforums.org/showpost.php?p=728541](http://ubuntuforums.org/showpost.php?p=728541)

It says to: 

"Open the Synaptic package manager. System --> Administration --> Synaptic Package Manager

If anything is broken it will tell you.
Choose 'Custom' from the buttons at the bottom then click on 'Broken'

Right click on the offending package and choose to remove it."

Unfortunately, Synaptic won't open.  If you have any ideas, I'd appreciate the help.

---

### Post by plucky on 2011-07-14
Open a Terminal **(Applications > Accessories > Terminal)** and run ```
sudo apt-get update
``` and post output to the forum.

Good Luck

---

### Post by Gen2ly on 2011-07-14
> **plucky said:**
> Open a Terminal **(Applications > Accessories > Terminal)** and run ```
sudo apt-get update
``` and post output to the forum.

Good Luck

eh, hope I don't require it :|

```
sudo apt-get update
[sudo] password for todd: 
Ign http://security.ubuntu.com natty-security InRelease
Ign http://us.archive.ubuntu.com natty InRelease
Ign http://us.archive.ubuntu.com natty-updates InRelease
Ign http://extras.ubuntu.com natty InRelease   
Hit http://security.ubuntu.com natty-security Release.gpg
Hit http://us.archive.ubuntu.com natty Release.gpg
Get:1 http://extras.ubuntu.com natty Release.gpg [72 B]
Hit http://security.ubuntu.com natty-security Release
Hit http://us.archive.ubuntu.com natty-updates Release.gpg
Hit http://extras.ubuntu.com natty Release                            
Hit http://us.archive.ubuntu.com natty Release                        
Hit http://us.archive.ubuntu.com natty-updates Release                
Hit http://security.ubuntu.com natty-security/main Sources            
Hit http://extras.ubuntu.com natty/main Sources                                
Hit http://security.ubuntu.com natty-security/restricted Sources               
Hit http://security.ubuntu.com natty-security/universe Sources        
Hit http://security.ubuntu.com natty-security/multiverse Sources      
Hit http://security.ubuntu.com natty-security/main i386 Packages      
Hit http://us.archive.ubuntu.com natty/main Sources                            
Hit http://extras.ubuntu.com natty/main i386 Packages                
Ign http://extras.ubuntu.com natty/main TranslationIndex
Hit http://security.ubuntu.com natty-security/restricted i386 Packages
Hit http://security.ubuntu.com natty-security/universe i386 Packages
Hit http://security.ubuntu.com natty-security/multiverse i386 Packages
Ign http://security.ubuntu.com natty-security/main TranslationIndex
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex
Ign http://security.ubuntu.com natty-security/universe TranslationIndex
Hit http://us.archive.ubuntu.com natty/restricted Sources            
Hit http://us.archive.ubuntu.com natty/universe Sources              
Hit http://us.archive.ubuntu.com natty/multiverse Sources            
Hit http://us.archive.ubuntu.com natty/main i386 Packages            
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages      
Hit http://us.archive.ubuntu.com natty/universe i386 Packages        
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages      
Ign http://us.archive.ubuntu.com natty/main TranslationIndex         
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex   
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex   
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex     
Hit http://us.archive.ubuntu.com natty-updates/main Sources          
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources    
Hit http://us.archive.ubuntu.com natty-updates/universe Sources      
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources    
Hit http://us.archive.ubuntu.com natty-updates/main i386 Packages    
Hit http://us.archive.ubuntu.com natty-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex 
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex
Ign http://extras.ubuntu.com natty/main Translation-en_US            
Ign http://extras.ubuntu.com natty/main Translation-en               
Ign http://security.ubuntu.com natty-security/main Translation-en_US
Ign http://security.ubuntu.com natty-security/main Translation-en
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com natty-security/multiverse Translation-en
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US
Ign http://security.ubuntu.com natty-security/restricted Translation-en
Ign http://security.ubuntu.com natty-security/universe Translation-en_US
Ign http://security.ubuntu.com natty-security/universe Translation-en
Ign http://us.archive.ubuntu.com natty/main Translation-en_US
Ign http://us.archive.ubuntu.com natty/main Translation-en
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty/restricted Translation-en
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty/universe Translation-en
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en
Fetched 72 B in 3s (19 B/s)
Reading package lists... Done
```

Hmm, nothing of any significance, looks like.  Any other thoughts?

Opp, just tested Synaptic again and it's working.  Thanks plucky.

---

