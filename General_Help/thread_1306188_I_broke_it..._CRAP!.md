---
title: "I broke it... CRAP!"
date: 2009-10-30
forum: General Help
---

### Post by mvalenti on 2009-10-30
Well with lots of help from great people on the forum, I got my machine running pretty sweet for about a week... Then I managed to break it... I think it was after I was playing with compiz.... I noticed the machine locking up... then getting some weird messages at restart of course i didnt write them down... Well now I get this message about packages...

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty-updates_multiverse_binary-amd64_Packages (1), E:The package lists or status file could not be parsed or opened.'

I cant run apt-get from the terminal either... the following is my attempt at clean up.

mark@mark-laptop:~$ sudo apt-get update
[sudo] password for mark: 
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US              
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg [307B]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [65.9kB]                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages [2915B]                     
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources [1192B]                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US           
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg [189B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security Release.gpg                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/multiverse Translation-en_US  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release [57.9kB]             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages                    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Sources                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Sources                      
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages [198kB]        
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages [2610B]  
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources [509B]    
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources [56.0kB]       
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources [2505B]  
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources [24.2kB]   
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages [85.4kB]  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/multiverse Packages
Fetched 497kB in 32s (15.3kB/s)
Reading package lists... Error!
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty-updates_multiverse_binary-amd64_Packages (1)
E: The package lists or status file could not be parsed or opened.
mark@mark-laptop:~$ sudo apt-get autoclean
Reading package lists... Error!
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty-updates_multiverse_binary-amd64_Packages (1)
E: The package lists or status file could not be parsed or opened.
mark@mark-laptop:~$ sudo apt-get -f install
Reading package lists... Error!
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty-updates_multiverse_binary-amd64_Packages (1)
E: The package lists or status file could not be parsed or opened.
mark@mark-laptop:~$ apt-cache packages
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty-updates_multiverse_binary-amd64_Packages (1)
mark@mark-laptop:~$ 


I would like to try to fix this in place of a reinstall, I feel it would help me more as a user...


-Regards,

Mark

---

### Post by phillw on 2009-10-30
Hi,

try 

```
sudo apt-get autoclean
```
and
```
sudo apt-get autoremove
```

Phill.

---

### Post by phillw on 2009-10-30
Here's one that was broken earlier ...

[http://ubuntuforums.org/showthread.php?p=7997001](http://ubuntuforums.org/showthread.php?p=7997001)

That one should sort you out :D

Phill.

---

### Post by mvalenti on 2009-10-30
> **phillw said:**
> Hi,

try 

```
sudo apt-get autoclean
```
and
```
sudo apt-get autoremove
```

Phill.

Thanks Phill,

I did try the autoclean and got errors, so I tried again, after reboot...

mark@mark-laptop:~$ sudo apt-get autoclean
[sudo] password for mark: 
Reading package lists... Error!
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty-updates_multiverse_binary-amd64_Packages (1)
E: The package lists or status file could not be parsed or opened.
mark@mark-laptop:~



mark@mark-laptop:~$ sudo apt-get autoclean
[sudo] password for mark: 
Reading package lists... Error!
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty-updates_multiverse_binary-amd64_Packages (1)
E: The package lists or status file could not be parsed or opened.
mark@mark-laptop:~

Still trying.. thanks for the feedback

---

### Post by mvalenti on 2009-10-30
> **phillw said:**
> Here's one that was broken earlier ...

[http://ubuntuforums.org/showthread.php?p=7997001](http://ubuntuforums.org/showthread.php?p=7997001)

That one should sort you out :D

Phill.

That worked! Thanks!

---

### Post by Gatemaze on 2009-10-30
although i do consider formatting/reinstalling an os (especially in linux where there are workarounds) if you only been running it for a week it might be faster to go ahead...

btw can you please post the output of your sources.list?
```

cat /etc/apt/sources.list

```

---

### Post by phillw on 2009-10-30
> **mvalenti said:**
> That worked! Thanks!

please edit your 1st post in this thread and alter it to solved  :D

Phill.

---

