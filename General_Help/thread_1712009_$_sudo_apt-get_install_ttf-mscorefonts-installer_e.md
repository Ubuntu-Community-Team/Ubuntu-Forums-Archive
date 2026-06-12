---
title: "$ sudo apt-get install ttf-mscorefonts-installer error"
date: 2011-03-22
forum: General Help
---

### Post by cazazo on 2011-03-22
Hi, I was trying to install wine and got the following error on synaptic:
```
wine1.2:
 Depends: lib32nss-mdns (>=0.10-3) but it is not installable
 Recommends: ttf-umefont  but it is not installable
 Recommends: ttf-mscorefonts-installer  but it is not installable
 Recommends: winbind  but it is not installable
 Recommends: wine1.2-gecko  but it is not installable
```

So, I tried to install the ttf-mscorefonts-installer from the terminal with no success:

```
sudo apt-get install ttf-mscorefonts-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ttf-mscorefonts-installer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'ttf-mscorefonts-installer' has no installation candidate
```
 I google it and tried everything not having the problem solved.
Any ideas??

---

### Post by kerry_s on 2011-03-22
Just install "ubuntu-restricted-extras" & get all that stuff out of the way.

---

### Post by cazazo on 2011-03-22
> **kerry_s said:**
> Just install "ubuntu-restricted-extras" & get all that stuff out of the way.

I tried that... didn't work!


```
sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ubuntu-restricted-extras
```

also tried:

```
sudo apt-get update
sudo apt-get upgrade --fix-broken
sudo dpkg --configure -a
sudo fc-cache -fv
sudo apt-get -f install
sudo apt-get install --reinstall ttf-mscorefonts-installer
sudo dpkg-reconfigure fontconfig
```

and nothing!

---

### Post by mcduck on 2011-03-22
Could you post the output of "sudo apt-get update"?

Since no package seems to be avaiable you clearly have problem with getting a connection to the repositories in the first place...

---

### Post by cazazo on 2011-03-22
> **mcduck said:**
> Could you post the output of "sudo apt-get update"?

Since no package seems to be avaiable you clearly have problem with getting a connection to the repositories in the first place...

There it goes...

```
Hit http://mirror.optus.net julia Release.gpg
Ign http://mirror.optus.net/linuxmint/packages/ julia/backport Translation-en                                                      
Ign http://mirror.optus.net/linuxmint/packages/ julia/backport Translation-en_US                                                   
Ign http://mirror.optus.net/linuxmint/packages/ julia/import Translation-en                                                        
Ign http://mirror.optus.net/linuxmint/packages/ julia/import Translation-en_US                                                     
Ign http://mirror.optus.net/linuxmint/packages/ julia/main Translation-en                                                          
Ign http://mirror.optus.net/linuxmint/packages/ julia/main Translation-en_US                                                       
Ign http://mirror.optus.net/linuxmint/packages/ julia/romeo Translation-en                                                         
Ign http://mirror.optus.net/linuxmint/packages/ julia/romeo Translation-en_US                                                      
Ign http://mirror.optus.net/linuxmint/packages/ julia/upstream Translation-en                                                      
Ign http://mirror.optus.net/linuxmint/packages/ julia/upstream Translation-en_US                                                   
Hit http://mirror.optus.net julia Release                                                                                          
Ign http://mirror.optus.net julia/main Sources                                                                               
Hit http://download.virtualbox.org maverick Release.gpg                                                
Ign http://mirror.optus.net julia/upstream Sources                                                     
Ign http://mirror.optus.net julia/import Sources                                                       
Ign http://mirror.optus.net julia/backport Sources                                                                           
Ign http://mirror.optus.net julia/romeo Sources                                                                              
Ign http://mirror.optus.net julia/main amd64 Packages                                                  
Ign http://mirror.optus.net julia/upstream amd64 Packages                                              
Ign http://mirror.optus.net julia/import amd64 Packages                                                
Ign http://mirror.optus.net julia/backport amd64 Packages                                                                    
Ign http://mirror.optus.net julia/romeo amd64 Packages                                                                       
Ign http://mirror.optus.net julia/main Sources                                                         
Ign http://mirror.optus.net julia/upstream Sources                                                     
Ign http://mirror.optus.net julia/import Sources                                                                             
Ign http://mirror.optus.net julia/backport Sources                                                                           
Ign http://mirror.optus.net julia/romeo Sources                                                        
Ign http://mirror.optus.net julia/main amd64 Packages                                                                        
Ign http://mirror.optus.net julia/upstream amd64 Packages                                                                    
Ign http://mirror.optus.net julia/import amd64 Packages                                                
Ign http://mirror.optus.net julia/backport amd64 Packages                                                                    
Hit http://deb.playonlinux.com maverick Release.gpg                                                                          
Ign http://deb.playonlinux.com/ maverick/main Translation-en                                           
Ign http://mirror.optus.net julia/romeo amd64 Packages                                                 
Hit http://mirror.optus.net julia/main Sources                                                         
Hit http://mirror.optus.net julia/upstream Sources                                                     
Ign http://download.virtualbox.org/virtualbox/debian/ maverick/contrib Translation-en                  
Ign http://download.virtualbox.org/virtualbox/debian/ maverick/contrib Translation-en_US               
Hit http://mirror.optus.net julia/import Sources                                 
Hit http://mirror.optus.net julia/backport Sources                               
Hit http://mirror.optus.net julia/romeo Sources                                                        
Hit http://mirror.optus.net julia/main amd64 Packages                                                  
Hit http://mirror.optus.net julia/upstream amd64 Packages                                              
Hit http://mirror.optus.net julia/import amd64 Packages                                                
Hit http://mirror.optus.net julia/backport amd64 Packages                                              
Hit http://mirror.optus.net julia/romeo amd64 Packages                                                 
Hit http://download.virtualbox.org maverick Release                              
Ign http://deb.playonlinux.com/ maverick/main Translation-en_US                  
Hit http://download.virtualbox.org maverick/contrib amd64 Packages               
Hit http://deb.playonlinux.com maverick Release                                  
Ign http://deb.playonlinux.com maverick/main amd64 Packages                      
Ign http://deb.playonlinux.com maverick/main amd64 Packages
Get:1 http://dl.google.com stable Release.gpg [197B]       
Hit http://deb.playonlinux.com maverick/main amd64 Packages                           
Hit http://ppa.launchpad.net maverick Release.gpg                                     
Ign http://ppa.launchpad.net/banshee-team/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/banshee-team/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/ maverick/main Translation-en                                              
Ign http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/ maverick/main Translation-en_US                                           
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                  
Ign http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/ maverick/main Translation-en                                                
Ign http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/ maverick/main Translation-en_US                                             
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                  
Ign http://ppa.launchpad.net/pmcenery/ppa/ubuntu/ maverick/main Translation-en                                                     
Ign http://ppa.launchpad.net/pmcenery/ppa/ubuntu/ maverick/main Translation-en_US                                                  
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                  
Ign http://ppa.launchpad.net/screenlets-dev/ppa/ubuntu/ maverick/main Translation-en                                               
Ign http://ppa.launchpad.net/screenlets-dev/ppa/ubuntu/ maverick/main Translation-en_US                                            
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                  
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en                                                    
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_US                                                 
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                  
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en                                                  
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en_US                                               
Hit http://ppa.launchpad.net maverick Release                                                                                      
Hit http://ppa.launchpad.net maverick Release                                                                                      
Hit http://ppa.launchpad.net maverick Release                                                                                      
Hit http://ppa.launchpad.net maverick Release                                                                                      
Hit http://ppa.launchpad.net maverick Release                                                                                      
Hit http://ppa.launchpad.net maverick Release                                                                                      
Hit http://ppa.launchpad.net maverick Release                                                                                      
Hit http://ppa.launchpad.net maverick/main amd64 Packages                                                                          
Hit http://ppa.launchpad.net maverick/main amd64 Packages                                                                          
Hit http://ppa.launchpad.net maverick/main amd64 Packages                                                                          
Hit http://ppa.launchpad.net maverick/main Sources                                                                                 
Hit http://ppa.launchpad.net maverick/main amd64 Packages                                                                          
Hit http://ppa.launchpad.net maverick/main amd64 Packages                                                                          
Hit http://ppa.launchpad.net maverick/main amd64 Packages                                                                          
Hit http://ppa.launchpad.net maverick/main Sources                                                                                 
Hit http://ppa.launchpad.net maverick/main amd64 Packages                                                                          
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en                                                              
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US
Get:2 http://dl.google.com stable Release.gpg [197B]
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en                                                          
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_US
Get:3 http://dl.google.com stable Release [1,347B]
Get:4 http://dl.google.com stable Release [1,347B]
Get:5 http://dl.google.com stable/main amd64 Packages [1,083B]
Get:6 http://dl.google.com stable/main amd64 Packages [761B]                                                                       
Fetched 4,932B in 1min 11s (69B/s)                                                                                                 
Reading package lists... Done

```

---

### Post by Joeb454 on 2011-03-22
Are you running Mint, by any chance? I'm not sure they'll have it in the repo's.

Either way, I think the package you're after is msttcorefonts, so try ```
sudo apt-get install msttcorefonts
```

---

### Post by cazazo on 2011-03-22
> **Joeb454 said:**
> Are you running Mint, by any chance? I'm not sure they'll have it in the repo's.

Either way, I think the package you're after is msttcorefonts, so try ```
sudo apt-get install msttcorefonts
```

Yes, I'm running Mint 10... I had tried that before and did not work!

```
$ sudo apt-get install msttcorefonts
[sudo] password for cazazo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'msttcorefonts' has no installation candidate

```

---

### Post by howefield on 2011-03-22
Have you the multiverse repository enabled ?

[http://packages.ubuntu.com/maverick/ttf-mscorefonts-installer](http://packages.ubuntu.com/maverick/ttf-mscorefonts-installer)


```
sudo apt-get install ttf-mscorefont-installer
```

---

### Post by cazazo on 2011-03-22
> **howefield said:**
> Have you the multiverse repository enabled ?

[http://packages.ubuntu.com/maverick/ttf-mscorefonts-installer](http://packages.ubuntu.com/maverick/ttf-mscorefonts-installer)


```
sudo apt-get install ttf-mscorefont-installer
```

Not sure if I do... how do I check for that???

---

### Post by kerry_s on 2011-03-22
Look for software sources in your menu.

---

### Post by cazazo on 2011-03-22
> **kerry_s said:**
> Look for software sources in your menu.

I don't think I do have it...

---

### Post by cazazo on 2011-04-03
Never mind! I reinstall the ubuntu 10.10... no other choice... Thanks every one!

---

