---
title: "Can't Install Apps in Software Center"
date: 2011-08-01
forum: General Help
---

### Post by Gerffy on 2011-08-01
Well herro, I've just upgraded to 11.04 and loving it but, now I can't add any apps through Ubuntu Software Center. I select an app and then click Install. After that, I get this:

An unhandable error occured
There seems to be a programming error in aptdaemon. The software that allows you to install/remove software and to perform other package management related tasks.

Then this window pops up:

System program problem detected
Do you want to report the problem now?


Now, when I choose to report the problem, I get another window:

Sorry, the program "aptd" closed unexpectedly.
I tried to use ```
sudo apt-get upgrade
```,and errors ```
javi@javi-Cpu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.
``` 
Tried to use apt-get -f install. 
```
javi@javi-Cpu:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
``` Yes I'm the Admin of my Computer. 
sudo apt-get update 
```
javi@javi-Cpu:~$ sudo apt-get update
Ign http://download.virtualbox.org natty InRelease
Hit http://download.virtualbox.org natty Release.gpg                           
Hit http://download.virtualbox.org natty Release                               
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://archive.canonical.com natty InRelease                               
Ign http://us.archive.ubuntu.com natty InRelease                               
Ign http://us.archive.ubuntu.com natty-updates InRelease                       
Ign http://security.ubuntu.com natty-security InRelease                        
Ign http://archive.ubuntu.com natty InRelease                                  
Ign http://archive.ubuntu.com natty-updates InRelease                          
Hit http://download.virtualbox.org natty/contrib i386 Packages                 
Ign http://download.virtualbox.org natty/contrib TranslationIndex              
Ign http://ppa.launchpad.net natty InRelease                                   
Hit http://extras.ubuntu.com natty Release.gpg                                 
Hit http://archive.canonical.com natty Release.gpg                             
Hit http://us.archive.ubuntu.com natty Release.gpg                             
Hit http://security.ubuntu.com natty-security Release.gpg                      
Hit http://archive.ubuntu.com natty Release.gpg                                
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://extras.ubuntu.com natty Release                                     
Hit http://security.ubuntu.com natty-security Release                          
Hit http://archive.canonical.com natty Release                                 
Hit http://us.archive.ubuntu.com natty-updates Release.gpg                     
Hit http://archive.ubuntu.com natty-updates Release.gpg                        
Hit http://ppa.launchpad.net natty Release                                     
Hit http://us.archive.ubuntu.com natty Release                                 
Hit http://archive.ubuntu.com natty Release                                    
Hit http://extras.ubuntu.com natty/main Sources                                
Hit http://security.ubuntu.com natty-security/main Sources                     
Hit http://archive.canonical.com natty/partner Sources                         
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://us.archive.ubuntu.com natty-updates Release                         
Hit http://archive.ubuntu.com natty-updates Release                            
Hit http://extras.ubuntu.com natty/main i386 Packages                          
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Ign http://download.virtualbox.org natty/contrib Translation-en_US             
Hit http://security.ubuntu.com natty-security/restricted Sources               
Hit http://security.ubuntu.com natty-security/universe Sources                 
Hit http://security.ubuntu.com natty-security/multiverse Sources               
Hit http://security.ubuntu.com natty-security/main i386 Packages               
Hit http://security.ubuntu.com natty-security/restricted i386 Packages         
Hit http://archive.canonical.com natty/partner i386 Packages                   
Ign http://archive.canonical.com natty/partner TranslationIndex                
Ign http://download.virtualbox.org natty/contrib Translation-en                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://us.archive.ubuntu.com natty/main Sources                            
Hit http://us.archive.ubuntu.com natty/restricted Sources                      
Hit http://us.archive.ubuntu.com natty/universe Sources                        
Hit http://us.archive.ubuntu.com natty/multiverse Sources                      
Hit http://us.archive.ubuntu.com natty/main i386 Packages                      
Hit http://archive.ubuntu.com natty/main Sources                               
Hit http://archive.ubuntu.com natty/restricted Sources                         
Hit http://archive.ubuntu.com natty/main i386 Packages                         
Hit http://archive.ubuntu.com natty/restricted i386 Packages                   
Ign http://archive.ubuntu.com natty/main TranslationIndex                      
Hit http://security.ubuntu.com natty-security/universe i386 Packages           
Hit http://security.ubuntu.com natty-security/multiverse i386 Packages         
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex      
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages                
Hit http://us.archive.ubuntu.com natty/universe i386 Packages                  
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages                
Ign http://us.archive.ubuntu.com natty/main TranslationIndex                   
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex             
Ign http://archive.ubuntu.com natty/restricted TranslationIndex                
Hit http://archive.ubuntu.com natty-updates/main Sources                       
Hit http://archive.ubuntu.com natty-updates/restricted Sources                 
Hit http://archive.ubuntu.com natty-updates/main i386 Packages                 
Hit http://archive.ubuntu.com natty-updates/restricted i386 Packages           
Ign http://archive.ubuntu.com natty-updates/main TranslationIndex              
Ign http://archive.ubuntu.com natty-updates/restricted TranslationIndex        
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
Ign http://archive.canonical.com natty/partner Translation-en_US               
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://extras.ubuntu.com natty/main Translation-en                         
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://security.ubuntu.com natty-security/main Translation-en_US           
Ign http://security.ubuntu.com natty-security/main Translation-en    
Ign http://archive.ubuntu.com natty/main Translation-en_US           
Ign http://archive.ubuntu.com natty/main Translation-en              
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com natty-security/multiverse Translation-en
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US
Ign http://security.ubuntu.com natty-security/restricted Translation-en
Ign http://security.ubuntu.com natty-security/universe Translation-en_US
Ign http://security.ubuntu.com natty-security/universe Translation-en
Ign http://archive.ubuntu.com natty/restricted Translation-en_US     
Ign http://archive.ubuntu.com natty/restricted Translation-en
Ign http://archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://archive.ubuntu.com natty-updates/main Translation-en
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en
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
Reading package lists... Done

```
Anyone and help would do me and trying to fix my problem.

---

### Post by Jouke S on 2011-08-01
```
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```
you can solve this error simply by closing the terminal if you're installing packages via software center, or by closing software center if you're installing packages via the terminal. 
-f should work then

---

### Post by Gerffy on 2011-08-01
Still getting this every time I try to install any program in Ubuntu Software Center. An unhandable error occured
There seems to be a programming error in aptdaemon. The software that allows you to install/remove software and to perform other package management related tasks.

Then this window pops up:

System program problem detected
Do you want to report the problem now?


Now, when I choose to report the problem, I get another window:

Sorry, the program "aptd" closed unexpectedly.
I'm just a newbie when it comes to ubuntu do I have to reinstall 11.04 natty or something?

---

