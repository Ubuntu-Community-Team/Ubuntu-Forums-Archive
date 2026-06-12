---
title: "bug report, update manager 9.04 -&gt; 9.10"
date: 2009-10-30
forum: General Help
---

### Post by FredWiersma on 2009-10-30
Update manager and 'sudo apt-get upgrade' both give the same message:

"sudo apt-get update
[I]Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty Release.gpg
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/main Translation-en_US      
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/universe Translation-en_US  
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release.gpg                                     
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Translation-en_US                          
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                                        
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US                          
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates Release.gpg                                
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/main Translation-en_US                     
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US               
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/universe Translation-en_US                 
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US               
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release                                         
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty Release                                            
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates Release                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                                     
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                                   
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/main Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/universe Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/universe Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
fred@fred-laptop:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
[/I]"

It seems the upgrader is looking for [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages) which doesn't exist.

What does exist is [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/) with some Packages files. What and where do I change the config file?

Thanks!
What is happening?

---

