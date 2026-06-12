---
title: "Cannot Run sudo apt-get update, Boot Problems"
date: 2010-03-19
forum: General Help
---

### Post by Joseph Schwenker on 2010-03-19
I tried to execute sudo apt-get update in the terminal today, and I got the following output:

```
joseph@ubuntu:~$ sudo apt-get update
[sudo] password for joseph: 
Get:1 http://dl.google.com stable Release.gpg [189B]
Hit http://us.archive.ubuntu.com karmic Release.gpg                            
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US                 
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US           
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://security.ubuntu.com karmic-security/main Translation-en_US          
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US    
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US             
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US           
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg                    
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US   
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US      
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com karmic-security Release                         
Hit http://us.archive.ubuntu.com karmic Release                                
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://us.archive.ubuntu.com karmic-updates Release                        
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://security.ubuntu.com karmic-security/main Packages                   
Ign http://ppa.launchpad.net karmic Release                                    
Hit http://us.archive.ubuntu.com karmic/main Packages                          
Hit http://us.archive.ubuntu.com karmic/restricted Packages                    
Hit http://us.archive.ubuntu.com karmic/main Sources                           
Hit http://us.archive.ubuntu.com karmic/restricted Sources                     
Hit http://us.archive.ubuntu.com karmic/universe Packages                      
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://ppa.launchpad.net karmic/main Sources                               
Hit http://security.ubuntu.com karmic-security/restricted Packages             
Hit http://security.ubuntu.com karmic-security/main Sources                    
Hit http://security.ubuntu.com karmic-security/restricted Sources              
Hit http://security.ubuntu.com karmic-security/universe Packages               
Hit http://us.archive.ubuntu.com karmic/universe Sources                       
Hit http://us.archive.ubuntu.com karmic/multiverse Packages                    
Hit http://us.archive.ubuntu.com karmic/multiverse Sources                     
Hit http://us.archive.ubuntu.com karmic-updates/main Packages                  
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages            
Hit http://us.archive.ubuntu.com karmic-updates/main Sources                   
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources             
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages              
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://security.ubuntu.com karmic-security/universe Sources                
Hit http://security.ubuntu.com karmic-security/multiverse Packages   
Hit http://security.ubuntu.com karmic-security/multiverse Sources    
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources     
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources
99% [Waiting for headers]                                                      


```

It stops at 99% [Waiting for headers], and does nothing.  I have been recently experiencing problems with booting as well.  I installed Ubuntu 9.10 64 bit using Wubi.  I tried to boot after turning off and on my computer (some updates had installed in my previous session that required a restart), and Ubuntu would not start.  It gave me the message:

```
error: You need to load the kernel first.

Press any key to continue..._
```

This happens when I try to start "Ubuntu, Linux 2.6.31-20-generic" and "Ubuntu, Linux 2.6.31-20-generic (recovery mode)".  I have to go down to the other option, "Ubuntu, Linux 2.6.31.14.generic", which works.  I have not tested 31.14.generic (recovery mode) yet.  Does anyone know how to solve these problems?  These might be related, as there may be some conflicting programs.  Some of my recent problems in Inkscape might also be caused by these problems.  Thanks!

---

### Post by Joseph Schwenker on 2010-03-20
bump

---

### Post by egalvan on 2010-03-20
> **Joseph Schwenker said:**
> I tried to execute sudo apt-get update in the terminal today, and I got the following output:

```
joseph@ubuntu:~$ sudo apt-get update

Get:1 http://dl.google.com stable Release.gpg [189B]

99% [Waiting for headers] 

```


How long did you wait at that "Waiting for headers" before "pulling the plug" ?

Sounds as if an update got interrupted.

---

### Post by Joseph Schwenker on 2010-03-20
I waited quite a while, although I'll try initiating the command, then letting the computer run for an hour.

---

### Post by Joseph Schwenker on 2010-03-20
I let the command run for half an hour, and it finished!  Here is the output:

```
joseph@ubuntu:~$ sudo apt-get update
[sudo] password for joseph: 
Get:1 http://dl.google.com stable Release.gpg [189B]
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://security.ubuntu.com karmic-security/main Translation-en_US          
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://us.archive.ubuntu.com karmic Release.gpg                            
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US                 
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US    
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US      
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com karmic-security Release                         
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US   
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US 
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg          
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg                      
Ign http://ppa.launchpad.net karmic/main Translation-en_US           
Get:2 http://ppa.launchpad.net karmic Release.gpg [307B]             
Ign http://ppa.launchpad.net karmic/main Translation-en_US           
Hit http://ppa.launchpad.net karmic Release.gpg                      
Ign http://ppa.launchpad.net karmic/main Translation-en_US           
Hit http://ppa.launchpad.net karmic Release                          
Hit http://us.archive.ubuntu.com karmic Release                                
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://us.archive.ubuntu.com karmic-updates Release                        
Ign http://ppa.launchpad.net karmic Release                                    
Hit http://security.ubuntu.com karmic-security/main Packages                   
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://ppa.launchpad.net karmic/main Sources                               
Hit http://us.archive.ubuntu.com karmic/main Packages                          
Hit http://us.archive.ubuntu.com karmic/restricted Packages                    
Hit http://us.archive.ubuntu.com karmic/main Sources                           
Hit http://us.archive.ubuntu.com karmic/restricted Sources                     
Hit http://us.archive.ubuntu.com karmic/universe Packages                      
Hit http://security.ubuntu.com karmic-security/restricted Packages             
Hit http://security.ubuntu.com karmic-security/main Sources                    
Hit http://security.ubuntu.com karmic-security/restricted Sources              
Hit http://security.ubuntu.com karmic-security/universe Packages               
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://us.archive.ubuntu.com karmic/universe Sources                       
Hit http://us.archive.ubuntu.com karmic/multiverse Packages          
Hit http://us.archive.ubuntu.com karmic/multiverse Sources           
Hit http://us.archive.ubuntu.com karmic-updates/main Packages        
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages  
Hit http://us.archive.ubuntu.com karmic-updates/main Sources         
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources   
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages    
Hit http://security.ubuntu.com karmic-security/universe Sources      
Hit http://security.ubuntu.com karmic-security/multiverse Packages   
Hit http://security.ubuntu.com karmic-security/multiverse Sources    
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources     
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources
Ign http://dl.google.com stable/main Translation-en_US                         
Get:3 http://dl.google.com stable Release [2,540B]
Get:4 http://dl.google.com stable/main Packages [911B]
Fetched 3,947B in 2min 0s (33B/s)                                              
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1FFD34C9EB13C954
joseph@ubuntu:~$ 

```

---

### Post by tommynz1975 on 2010-03-20
Having similar Issues in New Zealand
changed from Nz server to main. closed it. opened sources again changed back to new Zealand server.  are servers having an upgrade? or is their heavy demand for lucid so the servers are drained??

Sudo apt-get update gives me this.  On another system in the house for sudo apt-get dist-upgrade on  anew install I am averaging only 30kb/sec

> sudo apt-get update
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_NZ                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                            
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty Release.gpg                         
  Could not connect to nz.archive.ubuntu.com:80 (202.7.6.10), connection timed out
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/main Translation-en_NZ
  Unable to connect to nz.archive.ubuntu.com http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/restricted Translation-en_NZ
  Unable to connect to nz.archive.ubuntu.com http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/universe Translation-en_NZ
  Unable to connect to nz.archive.ubuntu.com http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/multiverse Translation-en_NZ
  Unable to connect to nz.archive.ubuntu.com http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates Release.gpg
  Unable to connect to nz.archive.ubuntu.com http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/main Translation-en_NZ
  Unable to connect to nz.archive.ubuntu.com http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/restricted Translation-en_NZ
  Unable to connect to nz.archive.ubuntu.com http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/universe Translation-en_NZ
  Unable to connect to nz.archive.ubuntu.com http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_NZ
  Unable to connect to nz.archive.ubuntu.com http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security Release.gpg
  Unable to connect to nz.archive.ubuntu.com http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security/main Translation-en_NZ
  Unable to connect to nz.archive.ubuntu.com http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security/restricted Translation-en_NZ
  Unable to connect to nz.archive.ubuntu.com http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security/universe Translation-en_NZ
  Unable to connect to nz.archive.ubuntu.com http:
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security/multiverse Translation-en_NZ
  Unable to connect to nz.archive.ubuntu.com http:
Reading package lists... Done                         
W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://nz.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not connect to nz.archive.ubuntu.com:80 (202.7.6.10), connection timed out

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_NZ.bz2](http://nz.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_NZ.bz2)  Unable to connect to nz.archive.ubuntu.com http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_NZ.bz2](http://nz.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_NZ.bz2)  Unable to connect to nz.archive.ubuntu.com http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_NZ.bz2](http://nz.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_NZ.bz2)  Unable to connect to nz.archive.ubuntu.com http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_NZ.bz2](http://nz.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_NZ.bz2)  Unable to connect to nz.archive.ubuntu.com http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg](http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg)  Unable to connect to nz.archive.ubuntu.com http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_NZ.bz2](http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_NZ.bz2)  Unable to connect to nz.archive.ubuntu.com http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_NZ.bz2](http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_NZ.bz2)  Unable to connect to nz.archive.ubuntu.com http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_NZ.bz2](http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_NZ.bz2)  Unable to connect to nz.archive.ubuntu.com http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_NZ.bz2](http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_NZ.bz2)  Unable to connect to nz.archive.ubuntu.com http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg](http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg)  Unable to connect to nz.archive.ubuntu.com http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_NZ.bz2](http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_NZ.bz2)  Unable to connect to nz.archive.ubuntu.com http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_NZ.bz2](http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_NZ.bz2)  Unable to connect to nz.archive.ubuntu.com http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_NZ.bz2](http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_NZ.bz2)  Unable to connect to nz.archive.ubuntu.com http:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_NZ.bz2](http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_NZ.bz2)  Unable to connect to nz.archive.ubuntu.com http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems


---

### Post by tommynz1975 on 2010-03-20
Joseph

Others have posted with this problem and a solution given was to run in terminal

```
sudo dpkg --configure -a
```
[sudo] password for User: 
```
 sudo apt-get update && sudo apt-get dist-upgrade
```

the && command allows you to run two commands on the same line.

The solution came from this link in General Forums.
[http://ubuntuforums.org/showthread.php?p=9001339#post9001339](http://ubuntuforums.org/showthread.php?p=9001339#post9001339)

Unfortunately I personally still have rubbish download speeds.

---

### Post by Joseph Schwenker on 2010-03-21
I think I already tried sudo dpkg --configure -a (I remember entering all the time back in 7.10!), but I'll try again.  Thanks for all of your help!

---

### Post by Joseph Schwenker on 2010-03-28
I am still having the "You need to start the kernel first" error message in GRUB.  Any solutions?

---

### Post by KingOfDeath on 2010-03-28
same thing here
```
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid Release.gpg
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/main Translation-fr
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/restricted Translation-fr
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid Release
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/main Packages
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/restricted Packages
Err cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/main Packages
  Veuillez utiliser apt-cdrom afin de faire reconnaître ce cédérom par votre APT. apt-get update ne peut être employé pour ajouter de nouveaux cédéroms
Err cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/restricted Packages
  Veuillez utiliser apt-cdrom afin de faire reconnaître ce cédérom par votre APT. apt-get update ne peut être employé pour ajouter de nouveaux cédéroms
Atteint http://sa.archive.ubuntu.com intrepid Release.gpg                      
Atteint http://sa.archive.ubuntu.com intrepid/main Translation-fr              
Atteint http://security.ubuntu.com intrepid-security Release.gpg               
Ign http://security.ubuntu.com intrepid-security/main Translation-fr           
Ign http://ppa.launchpad.net gutsy Release.gpg                                 
Ign http://ppa.launchpad.net gutsy/main Translation-fr                         
Atteint http://sa.archive.ubuntu.com intrepid/restricted Translation-fr        
Atteint http://sa.archive.ubuntu.com intrepid/universe Translation-fr          
Atteint http://sa.archive.ubuntu.com intrepid/multiverse Translation-fr        
Atteint http://sa.archive.ubuntu.com intrepid-updates Release.gpg              
Atteint http://sa.archive.ubuntu.com intrepid-updates/main Translation-fr      
Atteint http://sa.archive.ubuntu.com intrepid-updates/restricted Translation-fr
Atteint http://sa.archive.ubuntu.com intrepid-updates/universe Translation-fr  
Atteint http://sa.archive.ubuntu.com intrepid-updates/multiverse Translation-fr
Atteint http://sa.archive.ubuntu.com intrepid-backports Release.gpg            
Ign http://sa.archive.ubuntu.com intrepid-backports/main Translation-fr        
Atteint http://deb.opera.com stable Release.gpg                                
Ign http://deb.opera.com stable/non-free Translation-fr                        
Ign http://deb.playonlinux.com intrepid Release.gpg                            
Ign http://security.ubuntu.com intrepid-security/restricted Translation-fr     
Ign http://security.ubuntu.com intrepid-security/universe Translation-fr       
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-fr     
Réception de*: 1 http://ppa.launchpad.net intrepid Release.gpg [307B]          
Ign http://ppa.launchpad.net intrepid/main Translation-fr                      
Réception de*: 2 http://ppa.launchpad.net hardy Release.gpg [307B]             
Ign http://ppa.launchpad.net hardy/main Translation-fr                         
Réception de*: 3 http://ppa.launchpad.net intrepid Release.gpg [307B]          
Ign http://ppa.launchpad.net intrepid/main Translation-fr                      
Ign http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://deb.playonlinux.com intrepid/main Translation-fr                    
Atteint http://security.ubuntu.com intrepid-security Release                   
Réception de*: 4 http://dl.google.com stable Release.gpg [189B]                
Ign http://sa.archive.ubuntu.com intrepid-backports/restricted Translation-fr  
Ign http://sa.archive.ubuntu.com intrepid-backports/universe Translation-fr    
Ign http://sa.archive.ubuntu.com intrepid-backports/multiverse Translation-fr  
Atteint http://sa.archive.ubuntu.com intrepid-proposed Release.gpg             
Atteint http://deb.opera.com stable Release                                    
Atteint http://akirad.cinelerra.org akirad-intrepid Release.gpg                
Ign http://akirad.cinelerra.org akirad-intrepid/main Translation-fr            
Réception de*: 5 http://wine.budgetdedicated.com intrepid Release.gpg [189B]   
Ign http://wine.budgetdedicated.com intrepid/main Translation-fr               
Atteint http://archive.getdeb.net karmic-getdeb Release.gpg                    
Ign http://archive.getdeb.net karmic-getdeb/apps Translation-fr                
Atteint http://sa.archive.ubuntu.com intrepid-proposed/restricted Translation-fr
Atteint http://sa.archive.ubuntu.com intrepid-proposed/main Translation-fr     
Atteint http://sa.archive.ubuntu.com intrepid-proposed/multiverse Translation-fr
Atteint http://sa.archive.ubuntu.com intrepid-proposed/universe Translation-fr 
Atteint http://sa.archive.ubuntu.com intrepid Release                          
Atteint http://sa.archive.ubuntu.com intrepid-updates Release                  
Ign http://ppa.launchpad.net intrepid/main Translation-fr                      
Ign http://dl.google.com stable/main Translation-fr                            
Atteint http://security.ubuntu.com intrepid-security/main Packages             
Réception de*: 6 http://ppa.launchpad.net gutsy Release [27,6kB]               
Réception de*: 7 http://deb.playonlinux.com intrepid Release [1727B]           
Réception de*: 8 http://ppa.launchpad.net intrepid Release [65,9kB]            
Réception de*: 9 http://ppa.launchpad.net hardy Release [65,9kB]               
Réception de*: 10 http://ppa.launchpad.net intrepid Release [65,9kB]           
Ign http://ppa.launchpad.net intrepid Release                                  
Ign http://ppa.launchpad.net hardy Release                                     
Ign http://ppa.launchpad.net intrepid Release                                  
Atteint http://akirad.cinelerra.org akirad-intrepid Release                    
Ign http://archive.getdeb.net intrepid-getdeb Release.gpg                      
Ign http://archive.getdeb.net intrepid-getdeb/apps Translation-fr              
Ign http://deb.opera.com stable/non-free Packages                              
Atteint http://archive.getdeb.net karmic-getdeb Release                        
Atteint http://security.ubuntu.com intrepid-security/restricted Packages       
Atteint http://security.ubuntu.com intrepid-security/main Sources              
Atteint http://security.ubuntu.com intrepid-security/restricted Sources        
Réception de*: 11 http://wine.budgetdedicated.com intrepid Release [1025B]     
Réception de*: 12 http://ppa.launchpad.net intrepid Release [27,6kB]           
Atteint http://security.ubuntu.com intrepid-security/universe Packages         
Atteint http://security.ubuntu.com intrepid-security/universe Sources          
Atteint http://security.ubuntu.com intrepid-security/multiverse Packages       
Atteint http://security.ubuntu.com intrepid-security/multiverse Sources        
Réception de*: 13 http://dl.google.com stable Release [2540B]                  
Ign http://ppa.launchpad.net gutsy/main Packages                               
Ign http://ppa.launchpad.net gutsy/main Sources                                
Atteint http://deb.opera.com stable/non-free Packages                          
Ign http://archive.getdeb.net intrepid-getdeb Release                          
Ign http://deb.playonlinux.com intrepid/main Packages                          
Atteint http://akirad.cinelerra.org akirad-intrepid/main Packages              
Ign http://wine.budgetdedicated.com intrepid/main Packages                     
Atteint http://ppa.launchpad.net intrepid/main Packages                        
Atteint http://ppa.launchpad.net intrepid/main Sources                         
Atteint http://ppa.launchpad.net hardy/main Packages                           
Atteint http://ppa.launchpad.net intrepid/main Packages                        
Ign http://ppa.launchpad.net intrepid/main Packages                            
Atteint http://ppa.launchpad.net gutsy/main Packages                           
Atteint http://deb.playonlinux.com intrepid/main Packages                      
Atteint http://sa.archive.ubuntu.com intrepid-backports Release                
Atteint http://sa.archive.ubuntu.com intrepid-proposed Release                 
Atteint http://ppa.launchpad.net gutsy/main Sources                            
Réception de*: 14 http://wine.budgetdedicated.com intrepid/main Packages [1285B]
Réception de*: 15 http://dl.google.com stable/main Packages [917B]             
Atteint http://archive.getdeb.net karmic-getdeb/apps Packages                  
Atteint http://sa.archive.ubuntu.com intrepid/main Packages                    
Atteint http://sa.archive.ubuntu.com intrepid/restricted Packages              
Atteint http://sa.archive.ubuntu.com intrepid/main Sources                     
Atteint http://sa.archive.ubuntu.com intrepid/restricted Sources               
Atteint http://sa.archive.ubuntu.com intrepid/universe Packages                
Atteint http://sa.archive.ubuntu.com intrepid/universe Sources                 
Atteint http://sa.archive.ubuntu.com intrepid/multiverse Packages              
Ign http://archive.getdeb.net intrepid-getdeb/apps Packages                    
Atteint http://sa.archive.ubuntu.com intrepid/multiverse Sources               
Atteint http://sa.archive.ubuntu.com intrepid-updates/main Packages            
Atteint http://sa.archive.ubuntu.com intrepid-updates/restricted Packages      
Atteint http://sa.archive.ubuntu.com intrepid-updates/main Sources             
Atteint http://sa.archive.ubuntu.com intrepid-updates/restricted Sources       
Atteint http://sa.archive.ubuntu.com intrepid-updates/universe Packages        
Atteint http://sa.archive.ubuntu.com intrepid-updates/universe Sources         
Atteint http://ppa.launchpad.net intrepid/main Packages                        
Atteint http://sa.archive.ubuntu.com intrepid-updates/multiverse Packages      
Atteint http://sa.archive.ubuntu.com intrepid-updates/multiverse Sources       
Atteint http://sa.archive.ubuntu.com intrepid-backports/main Packages          
Atteint http://sa.archive.ubuntu.com intrepid-backports/restricted Packages    
Err http://archive.getdeb.net intrepid-getdeb/apps Packages                    
  404 Not Found
Atteint http://sa.archive.ubuntu.com intrepid-backports/universe Packages      
Atteint http://sa.archive.ubuntu.com intrepid-backports/multiverse Packages    
Atteint http://sa.archive.ubuntu.com intrepid-proposed/restricted Packages     
Atteint http://sa.archive.ubuntu.com intrepid-proposed/main Packages           
Atteint http://sa.archive.ubuntu.com intrepid-proposed/multiverse Packages     
Atteint http://sa.archive.ubuntu.com intrepid-proposed/universe Packages       
Atteint http://archive.canonical.com intrepid Release.gpg                      
Ign http://archive.canonical.com intrepid/partner Translation-fr               
Atteint http://archive.canonical.com intrepid Release                      
Réception de*: 16 http://download.virtualbox.org intrepid Release.gpg [197B]   
Ign http://download.virtualbox.org intrepid/non-free Translation-fr        
Atteint http://archive.canonical.com intrepid/partner Packages             
Atteint http://archive.canonical.com intrepid/partner Sources              
Réception de*: 17 http://download.virtualbox.org intrepid Release [3456B]  
Ign http://download.virtualbox.org intrepid Release                        
Atteint http://download.virtualbox.org intrepid/non-free Packages
Err http://download.tuxfamily.org feisty-upure64 Release.gpg                   
  Connexion à download.tuxfamily.org:*80 (127.0.0.1) impossible. - connect (111 Connexion refusée)
Err http://download.tuxfamily.org feisty-upure64/main-amd64 Translation-fr     
  Connexion à download.tuxfamily.org:*80 (127.0.0.1) impossible. - connect (111 Connexion refusée)
Err http://download.tuxfamily.org feisty Release.gpg                           
  Connexion à download.tuxfamily.org:*80 (127.0.0.1) impossible. - connect (111 Connexion refusée)
Err http://download.tuxfamily.org feisty/eyecandy Translation-fr               
  Connexion à download.tuxfamily.org:*80 (127.0.0.1) impossible. - connect (111 Connexion refusée)
7270o réceptionnés en 10s (701o/s)                                             
Lecture des listes de paquets... Fait
W: GPG error: http://ppa.launchpad.net intrepid Release: Les signatures suivantes n'ont pas pu être vérifiées car la clé publique n'est pas disponible*: NO_PUBKEY 28A8205077558DD0
W: GPG error: http://ppa.launchpad.net hardy Release: Les signatures suivantes n'ont pas pu être vérifiées car la clé publique n'est pas disponible*: NO_PUBKEY 9423A34CCA967634
W: GPG error: http://ppa.launchpad.net intrepid Release: Les signatures suivantes n'ont pas pu être vérifiées car la clé publique n'est pas disponible*: NO_PUBKEY B5115B98AA836CA8
W: GPG error: http://download.virtualbox.org intrepid Release: Les signatures suivantes n'ont pas pu être vérifiées car la clé publique n'est pas disponible*: NO_PUBKEY DCF9F87B6DFBCBAE
W: Impossible de récupérer http://download.tuxfamily.org/upure64/dists/feisty-upure64/Release.gpg  Connexion à download.tuxfamily.org:*80 (127.0.0.1) impossible. - connect (111 Connexion refusée)

W: Impossible de récupérer http://download.tuxfamily.org/upure64/dists/feisty-upure64/main-amd64/i18n/Translation-fr.bz2  Connexion à download.tuxfamily.org:*80 (127.0.0.1) impossible. - connect (111 Connexion refusée)

W: Impossible de récupérer http://download.tuxfamily.org/3v1deb/dists/feisty/Release.gpg  Connexion à download.tuxfamily.org:*80 (127.0.0.1) impossible. - connect (111 Connexion refusée)

W: Impossible de récupérer http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/i18n/Translation-fr.bz2  Connexion à download.tuxfamily.org:*80 (127.0.0.1) impossible. - connect (111 Connexion refusée)

W: Impossible de récupérer cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Veuillez utiliser apt-cdrom afin de faire reconnaître ce cédérom par votre APT. apt-get update ne peut être employé pour ajouter de nouveaux cédéroms

W: Impossible de récupérer cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Veuillez utiliser apt-cdrom afin de faire reconnaître ce cédérom par votre APT. apt-get update ne peut être employé pour ajouter de nouveaux cédéroms

W: Impossible de récupérer http://archive.getdeb.net/ubuntu/dists/intrepid-getdeb/apps/binary-i386/Packages.gz  404 Not Found

W: Le téléchargement de quelques fichiers d'index a échoué, ils ont été ignorés, ou les anciens ont été utilisés à la place.
W: Duplicate sources.list entry http://archive.canonical.com intrepid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_intrepid_partner_binary-i386_Packages)
W: Duplicate sources.list entry http://wine.budgetdedicated.com intrepid/main Packages (/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_intrepid_main_binary-i386_Packages)
W: Vous pouvez lancer «*apt-get update*» pour corriger ces problèmes.

```
ik no one would get this but you can use a translator lol

---

### Post by KingOfDeath on 2010-03-29
> **pastalavista said:**
> I've discovered my culprit was the Google repositories I added when I installed the Chrome Browser. If I uncheck the Google repository in System-->Administration-->Software Sources, the update doesn't hang, but then I don't get Chrome updates either. I just check the box for that repo once or twice a month now.

:D Unistall Google Chrome that would be the reason.

---

### Post by Joseph Schwenker on 2010-03-29
I would try, but unfortunately, Ubuntu is currently refusing to use the default graphics driver.  I had an nVidia card in my machine, and took it out to put in another machine, and Ubuntu will not load the default configuration, the one for an integrated intel card.  The one in my machine is the Intel GMA 3100.  I have a thread on it [here]("http://ubuntuforums.org/showthread.php?t=1441564").

---

